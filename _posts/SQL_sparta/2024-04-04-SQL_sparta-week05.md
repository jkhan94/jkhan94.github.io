---
layout: post
title: SQL_sparta - week05
date: 2024-04-04
category: SQL_sparta
---

## week05.sql
```sql
-- 값이 없을 때 또는 null이 있을 경우.
-- 1. 값 변경. 특정 값일 경우 null로 변경
select restaurant_name,
       avg(rating) average_of_rating,
       avg(if(rating<>'Not given', rating, null)) average_of_rating2
from food_orders

-- 2. 값 제외. null이 아닌 값만 사용.
select a.order_id,
       a.customer_id,
       a.restaurant_name,
       a.price,
       b.name,
       b.age,
       b.gender
from food_orders a left join customers b on a.customer_id=b.customer_id
where b.customer_id is not null 

-- coalesce(age, 대체값)
-- customers에서 나이가 null일 경우 20으로 변경
select a.order_id,
       a.customer_id,
       a.restaurant_name,
       a.price,
       b.name,
       b.age,
       coalesce(b.age, 20) "null 제거",
       b.gender
from food_orders a left join customers b on a.customer_id=b.customer_id
where b.age is null

-- ------------------------------------------------------------------------
-- 이상한 값 처리법
-- 1. 조건문으로 값의 범위를 지정
-- 15세 미만이거나 80세 초과인 경우 15, 80으로 각각 대체
select customer_id, name, email, gender, age,
       case when age<15 then 15
            when age>80 then 80
            else age end "범위를 지정해준 age"
from customers

-- ------------------------------------------------------------------------
-- Pivot Table : 행, 열 모두 집계기준인 표
-- 음식점별 시간별 주문건수 Pivot Table 뷰 만들기 (15~20시 사이, 20시 주문건수 기준 내림차순)
-- 피벗 만들 베이스 데이터
select  fo.restaurant_name, 
		SUBSTRING(p.`time`,1,2) as order_hour,
		count(1)
from food_orders fo inner join payments p on fo.order_id = p.order_id 
where SUBSTRING(p.`time`,1,2) BETWEEN 15 and 20
group by fo.restaurant_name, order_hour
order by order_hour desc

select a.restaurant_name,
       substring(b.time, 1, 2) hh,
       count(1) cnt_order
from food_orders a inner join payments b on a.order_id=b.order_id
where substring(b.time, 1, 2) between 15 and 20
group by 1, 2

-- 피벗 테이블
-- 행 기준 = 열 1개
-- 열 기준 = 열 여러 개
-- 행 기준은 음식점명, 열 기준은 주문 시간
select restaurant_name,
       max(if(hh='15', cnt_order, 0)) as "15",
       max(if(hh='16', cnt_order, 0)) as "16",
       max(if(hh='17', cnt_order, 0)) as "17",
       max(if(hh='18', cnt_order, 0)) as "18",
       max(if(hh='19', cnt_order, 0)) as "19",
       max(if(hh='20', cnt_order, 0)) as "20"
from(
		select a.restaurant_name,
		       substring(b.time, 1, 2) hh,
		       count(1) cnt_order
		from food_orders a inner join payments b on a.order_id=b.order_id
		where substring(b.time, 1, 2) between 15 and 20
		group by 1, 2
	) a
group by 1
order by 7 desc

-- ------------------------------------------------------------------------
-- 성별, 연령별 주문건수 Pivot Table 뷰 만들기  (나이는 10~59세 사이, 연령 순으로 내림차순)
-- 베이스 데이터
-- 테이블에 존재하는 연령별 카운트. 남 33세, 여 33세, 남 45세, 여 45세...
select c.gender, c.age, count(1)
from customers c
inner join food_orders fo on c.customer_id = fo.customer_id
where c.age between 10 and 59
group by 1, 2
order by c.age

-- 연령대별 카운트. 남 10대, 여 10대, 남 20대, 여 20대...
select b.gender,
       case when age between 10 and 19 then 10
            when age between 20 and 29 then 20
            when age between 30 and 39 then 30
            when age between 40 and 49 then 40
            when age between 50 and 59 then 50 end age,
       count(1)
from food_orders a inner join customers b on a.customer_id=b.customer_id
where b.age between 10 and 59
group by 1, 2

-- 피벗 테이블
select gender,
	   max(if(age=50, cnt_order, 0)) as '50',  
	   max(if(age=40, cnt_order, 0)) as '40',
	   max(if(age=30, cnt_order, 0)) as '30',
	   sum(if(age=20, cnt_order, 0)) as '20',
	   max(if(age=10, cnt_order, 0)) as '10'   
from (
		select b.gender,
		       case when age between 10 and 19 then 10
		            when age between 20 and 29 then 20
		            when age between 30 and 39 then 30
		            when age between 40 and 49 then 40
		            when age between 50 and 59 then 50 end age,
		       count(1) as cnt_order
		from food_orders a inner join customers b on a.customer_id=b.customer_id
		where b.age between 10 and 59
		group by 1, 2
	 ) a 
group by 1


select age,
       max(if(gender='male', order_count, 0)) male,
       max(if(gender='female', order_count, 0)) female
from 
(
select b.gender,
       case when age between 10 and 19 then 10
            when age between 20 and 29 then 20
            when age between 30 and 39 then 30
            when age between 40 and 49 then 40
            when age between 50 and 59 then 50 end age,
       count(1) order_count
from food_orders a inner join customers b on a.customer_id=b.customer_id
where b.age between 10 and 59
group by 1, 2
) t
group by 1
order by 1 desc

-- ------------------------------------------------------------------------
-- 윈도우 함수
-- Rank
/*음식 타입별로 주문 건수가 가장 많은 상점 3개씩 조회*/
-- 음식 타입별 주문 건수
-- 음식 타입과 음식점명으로 그룹화하는 것.
select cuisine_type,
	   restaurant_name,
	   count(1) as order_count
from food_orders fo
group by 1, 2

-- 순위 rank 사용
-- cuisine_type기준으로 순위를 구한다. 순위는 order_count 내림차순.
select cuisine_type,
       restaurant_name,
       rank() over (partition by cuisine_type order by order_count desc) rn,
       order_count
from(
		select cuisine_type, restaurant_name, count(1) order_count
		from food_orders
		group by 1, 2
	) a

-- 음식점명 3개만 출력
select cuisine_type,
   	   restaurant_name,
       order_count,
       ranking "순위"
from (
		select cuisine_type,
		       restaurant_name,
		       rank() over (partition by cuisine_type order by order_count desc) ranking,
		       order_count
		from (
			select cuisine_type, restaurant_name, count(1) order_count
			from food_orders
			group by 1, 2
		) a
	 ) b
where ranking<=3
order by 1, 4
	
-- sum
-- 누적합, 카테고리별 합계와 원본 컬럼 같이 사용.
/*각 음식점의 주문건이 해당 음식 타입에서 차지하는 비율을 구하고, 주문건이 낮은 순으로 정렬했을 때 누적 합 구하기 */
-- 해당 음식 타입에서 각 음식점의 주문건수
select cuisine_type,
	   restaurant_name, 
	   count(1) cnt_order
from food_orders
group by 1, 2

-- 주문건이 낮은 순으로 정렬했을 때 누적 합
-- cnt_order가 모두 1이라서 우열을 가릴 수 없다. 그래서 누적합의 첫 값은 9
select cuisine_type,
       restaurant_name,
       cnt_order,
       sum(cnt_order) over (partition by cuisine_type) sum_cuisine_type,
       sum(cnt_order) over (partition by cuisine_type order by cnt_order) cumulative_sum
from (
		select cuisine_type, restaurant_name, count(1) cnt_order
		from food_orders
		group by 1, 2
	  ) a
order by 1, 3

-- ------------------------------------------------------------------------
-- 날짜
-- date(날짜 컬럼명) : 날짜 형식으로 변경.
select date(date) date_type,
       date
from payments

-- date type 을 date_format 을 이용하여 년, 월, 일, 주 로 조회
-- date_format(날짜 타입의 컬럼명, 형식)
/*1. 년 : Y (4자리), y(2자리)
2. 월 : M, m
3. 일 : d, e
4. 요일 : w */
/* 년도, 월을 포함하여 데이터 가공하기 */
select date(date) date_type,
       date_format(date(date), '%Y') "년",
       date_format(date(date), '%m') "월",
       date_format(date(date), '%d') "일",
       date_format(date(date), '%w') "요일"
from payments

/* 년도, 월별 주문건수 구하기 */
select date_format(date(date), '%Y') "년",
       date_format(date(date), '%m') "월",
       date_format(date(date), '%Y%m') "년월",
       COUNT(1) "주문건수"
from food_orders fo inner join payments p on fo.order_id=p.order_id
group by 1, 2, 3

/* 3월 조건으로 지정하고, 년도별로 정렬하기 */
select date_format(date(date), '%Y') "년",
       date_format(date(date), '%m') "월",
       date_format(date(date), '%Y%m') "년월",
       COUNT(1) "주문건수"
from food_orders fo inner join payments p on fo.order_id=p.order_id
where date_format(date(date), '%m') = '03'
group by 1, 2, 3
order by 1

-- ------------------------------------------------------------------------
/* 음식 타입별, 연령별 주문건수 pivot view 만들기 (연령은 10~59세 사이) */
 -- 음식 타입별, 연령별 주문건수
select 	fo.cuisine_type, 
		CASE 
			when c.age between 10 and 19 then 10
			when c.age between 20 and 29 then 20
			when c.age between 30 and 39 then 30
			when c.age between 40 and 49 then 40
			when c.age between 50 and 59 then 50
		END age,
		COUNT(1) cnt_order
from food_orders fo inner join customers c on fo.customer_id = c.customer_id
where c.age BETWEEN 10 and 59
group by 1, 2

-- pivot table
select cuisine_type,
	   max(if(age = 10, cnt_order, 0)) as '10',
	   max(if(age = 20, cnt_order, 0)) as '20',
	   max(if(age = 30, cnt_order, 0)) as '30',
	   max(if(age = 40, cnt_order, 0)) as '40',
	   max(if(age = 50, cnt_order, 0)) as '50'
from (
			select 	fo.cuisine_type, 
					CASE 
						when c.age between 10 and 19 then 10
						when c.age between 20 and 29 then 20
						when c.age between 30 and 39 then 30
						when c.age between 40 and 49 then 40
						when c.age between 50 and 59 then 50
					END age,
					COUNT(1) cnt_order
			from food_orders fo inner join customers c on fo.customer_id = c.customer_id
			where c.age BETWEEN 10 and 59
			group by 1, 2
	 ) a
group by 1


select cuisine_type,
       max(if(age=10, order_count, 0)) "10대",
       max(if(age=20, order_count, 0)) "20대",
       max(if(age=30, order_count, 0)) "30대",
       max(if(age=40, order_count, 0)) "40대",
       max(if(age=50, order_count, 0)) "50대"
from(
		select a.cuisine_type,
		       case when age between 10 and 19 then 10
		            when age between 20 and 29 then 20
		            when age between 30 and 39 then 30
		            when age between 40 and 49 then 40
		            when age between 50 and 59 then 50 end age,
		       count(1) order_count
		from food_orders a inner join customers b on a.customer_id=b.customer_id
		where age between 10 and 59
		group by 1, 2
	) t
group by 1
```
