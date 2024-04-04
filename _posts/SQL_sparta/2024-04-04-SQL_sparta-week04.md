---
layout: post
title: SQL_sparta - week04
date: 2024-04-04
category: SQL_sparta
---

## week04.sql
```sql
-- 서브쿼리
select price / quantity
from (select price, quantity from food_orders) a 

-- 주문 테이블에서  주문 번호, 음식점명, 음식 준비시간을 가져오기
select order_id, 
  	   restaurant_name, 
  	   food_preparation_time
from (select order_id, restaurant_name, food_preparation_time 
      from food_orders) a

-- 음식 주문시간이 25분보다 초과한 시간을 가져오기
select order_id, 
 	   restaurant_name, 
 	   food_preparation_time,
 	   if(over_time>=0, over_time, 0) over_time
from (select order_id, restaurant_name, food_preparation_time, 
	  food_preparation_time-25 as over_time 
      from food_orders) a

-- ----------------------------------------------------
-- User Segmentation과 서브쿼리
/*- 음식점의 평균 단가별 segmentation 을 진행하고, 그룹에 따라 수수료 연산하기    
(수수료 구간 - 
  ~5000원 미만 0.05%
  ~20000원 미만 1%
  ~30000원 미만 2%
  30000원 초과 3%)*/
      
-- 평균 단가별 음식점 분류
select restaurant_name, avg(price/quantity) 
from food_orders
group by restaurant_name    
  
-- 분류한 음식점별로 수수료율 계산
select restaurant_name, price_per_plate, 
	   CASE when price_per_plate < 5000 then 0.005
			when price_per_plate between 5000 and 19999 then 0.01
			when price_per_plate between 20000 and 29999 then 0.02
			when price_per_plate > 30000 then 0.03
	   end ratio
from (select restaurant_name, avg(price/quantity) price_per_plate
		from food_orders
		group by restaurant_name) a

-- 음식점명, 평균단가, 수수료 출력
select restaurant_name, price_per_plate, price_per_plate*ratio as "수수료"
from (select restaurant_name, price_per_plate, 
	   CASE when price_per_plate < 5000 then 0.005
			when price_per_plate between 5000 and 19999 then 0.01
			when price_per_plate between 20000 and 29999 then 0.02
			when price_per_plate > 30000 then 0.03
	   end ratio
from (select restaurant_name, avg(price/quantity) price_per_plate
		from food_orders
		group by restaurant_name) a) b

select restaurant_name,
       price_per_plate*ratio_of_add "수수료"
from 
	(select restaurant_name,
	        case when price_per_plate<5000 then 0.005
	            when price_per_plate between 5000 and 19999 then 0.01
	            when price_per_plate between 20000 and 29999 then 0.02
	            else 0.03 end ratio_of_add,
	        price_per_plate
	  from (select restaurant_name, avg(price/quantity) price_per_plate
			from food_orders
			group by 1) a 
	 ) b

-- ----------------------------------------------------
/*음식점의 지역과 평균 배달시간으로 segmentation 하기
20분 미만, 30분 미만, 30분 초과*/
select restaurant_name, SUBSTRING(addr,1,2), AVG(delivery_time) 
from food_orders
group by 1, 2

SELECT restaurant_name, region, avg_time,
		CASE 
			when avg_time <= 20 then '<=20'
			when avg_time > 20 and avg_time <=30 then '20< x <=30'
			else '>30'
		END delivery_range
from (select restaurant_name, SUBSTRING(addr,1,2) region, AVG(delivery_time) avg_time
	  from food_orders
	  group by 1, 2) a

select restaurant_name,
       sido,
       case when avg_time<=20 then '<=20'
            when avg_time>20 and avg_time <=30 then '20<x<=30'
            when avg_time>30 then '>30' end time_segment
from 
(
	select restaurant_name,
	       substring(addr, 1, 2) sido,
	       avg(delivery_time) avg_time
	from food_orders
	group by 1, 2
) a

-- ----------------------------------------------------
/*음식 타입별 총 주문수량과 음식점 수를 연산하고, 주문수량과 음식점 수별 수수료율을 산정하기
    (음식점수 5개 이상, 주문수 30개 이상 → 수수료 0.05%
     음식점수 5개 이상, 주문수 30개 미만 → 수수료 0.08%
     음식점수 5개 미만, 주문수 30개 이상 → 수수료 1%
     음식점수 5개 미만, 주문수 30개 미만 → 수수로 2%)*/

select cuisine_type, 
	   count_orders,
	   count_res,
       case when count_res>=5 and count_orders>=30 then 0.0005
            when count_res>=5 and count_orders<30 then 0.008
            when count_res<5 and count_orders>=30 then 0.01
            when count_res<5 and count_orders<30 then 0.02 end ratio_of_add
from
(
	select cuisine_type,
	       sum(quantity) as count_orders,
	       count(distinct restaurant_name) as count_res
	from food_orders
	group by 1
) a

-- ----------------------------------------------------
/*음식점의 총 주문수량과 주문 금액을 연산하고, 주문 수량을 기반으로 수수료 할인율 구하기
	(할인조건
	수량이 5개 이하 → 10%
	수량이 15개 초과, 총 주문금액이 300000 이상 → 0.5%
	이 외에는 일괄 1%)*/
SELECT restaurant_name, total_price, total_quantity,
CASE 
	when total_quantity <= 5 then 0.1
	when total_quantity > 15 and total_price >= 300000 then 0.005
	else 0.01
END discount_rate
from (
		select restaurant_name, sum(quantity) total_quantity, sum(price) total_price
		from food_orders
		group by restaurant_name
	 ) a

	 
 select restaurant_name, sum_price, sum_quantity,
  		case when sum_quantity<=5 then 0.1
	         when sum_quantity>15 and sum_price>=300000 then 0.005
     		 else 0.01 
 		 end ratio_of_add
from 
(	select restaurant_name,
	       sum(quantity) sum_quantity,
	       sum(price) sum_price
	from food_orders
	group by 1
) a

-- ----------------------------------------------------
-- left Join : 왼쪽 거 전부 출력, null
select *
from food_orders fo
left join payments pay 
on fo.order_id = pay.order_id 

-- inner join : 공통행만 출력
select *
from food_orders fo
inner join payments pay 
on fo.order_id = pay.order_id 

/*
주문 테이블과 고객 테이블을 cusomer_id 를 기준으로 left join 으로 묶어보기
(조회 컬럼 : order_id, customer_id, restaurant_name, price, name, age, gender)
*/
select a.order_id,
       a.customer_id,
       a.restaurant_name,
       a.price,
       b.name,
       b.age,
       b.gender
from food_orders a left join customers b on a.customer_id=b.customer_id

-- ----------------------------------------------------
/*
한국 음식의 주문별 결제 수단과 수수료율을 조회하기
    (조회 컬럼 : 주문 번호, 식당 이름, 주문 가격, 결제 수단, 수수료율)
    *결제 정보가 없는 경우도 포함하여 조회
*/
select fo.order_id, fo.restaurant_name, fo.price, p.pay_type, p.vat
from food_orders fo
left join payments p 
on fo.order_id = p.order_id 
where cuisine_type = 'Korean'

select a.order_id,
       a.restaurant_name,
       a.price,
       b.pay_type,
       b.vat
from food_orders a left join payments b on a.order_id=b.order_id
where cuisine_type='Korean'

-- ----------------------------------------------------
/* 고객의 주문 식당 조회하기
    (조회 컬럼 : 고객 이름, 연령, 성별, 주문 식당) 
    *고객명으로 정렬, 중복 없도록 조회
*/
select distinct c.name , c.age , c.gender , fo.restaurant_name 
from customers c
right join food_orders fo 
on c.customer_id = fo.customer_id
order by c.name 

select distinct c.name,
       c.age,
       c.gender,
       f.restaurant_name
from food_orders f left join customers c on f.customer_id=c.customer_id
order by c.name 

-- ----------------------------------------------------
/*주문 가격과 수수료율을 곱하여 주문별 수수료 구하기
(조회 컬럼 : 주문 번호, 식당 이름, 주문 가격, 수수료율, 수수료)
	*수수료율이 있는 경우만 조회
*/
select fo.order_id, fo.restaurant_name, fo.price, p.vat, 	  	   fo.price * p.vat as "수수료"
from food_orders fo
inner join payments p on fo.order_id = p.order_id 

select a.order_id,
       a.restaurant_name,
       a.price,
       b.vat,
       a.price*b.vat "수수료율"
from food_orders a inner join payments b on a.order_id=b.order_id

-- ----------------------------------------------------
/*50세 이상 고객의 연령에 따라 경로 할인율을 적용하고, 음식 타입별로 원래 가격과 할인 적용 가격 합을 구하기    
(조회 컬럼 : 음식 타입, 원래 가격, 할인 적용 가격, 할인 가격)
	*할인 : 나이-50*0.005
	*고객 정보가 없는 경우도 포함하여 조회, 할인 금액이 큰 순서대로 정렬
*/

-- 나이별 할인율
select fo.cuisine_type, fo.price, c.age,
	   if(c.age>=50, (c.age-50)*0.005, 0) as discount
from food_orders fo
left join customers c on
fo.customer_id = c.customer_id
order by discount desc

-- 음식 타입별로 원래 가격과 할인 적용 가격 합
-- 이건 전체 고객
select 	cuisine_type, 
		sum(price), 
		sum(price) - sum(price * discount) as "할인 적용 가격", 
		sum(price * discount) as "할인 가격"
from(
	select 	fo.cuisine_type, fo.price, c.age, 
			if(c.age >= 50,(c.age-50)* 0.005, 0) as discount
	from food_orders fo
		left join customers c on fo.customer_id = c.customer_id
	order by discount desc) a
group by cuisine_type
order by 4 desc

-- 고객은 50대 이상
select 	cuisine_type, 
		sum(price), 
		sum(price) - sum(price*discount) as "할인 적용 가격", 
		sum(price*discount) as "할인 가격"
from(
	select 	fo.cuisine_type, fo.price,
			(c.age-50)*0.005 as discount
	from food_orders fo
		inner join customers c on fo.customer_id = c.customer_id
	where c.age >= 50) a
group by cuisine_type
order by 4 desc


select cuisine_type,
       sum(price) "원래 가격",
       sum(price)-sum(discount_price) "할인 적용 가격",
       sum(discount_price) "할인 가격" 
from 
(
	select a.cuisine_type,
	       price,
	       price*((b.age-50)*0.005) discount_price
	from food_orders a inner join customers b on a.customer_id=b.customer_id
	where b.age>=50
) t
group by 1
order by 4 desc

-- ----------------------------------------------------
-- 숙제
/*식당별 평균 음식 주문 금액과 주문자의 평균 연령을 기반으로 Segmentation 하기
- 평균 음식 주문 금액 기준 : 5,000 / 10,000 / 30,000 / 30,000 초과
- 평균 연령 : ~ 20대 / 30대 / 40대 / 50대 이상
- 두 테이블 모두에 데이터가 있는 경우만 조회, 식당 이름 순으로 오름차순 정렬
*/
-- 식당별 평균 음식 주문 금액, 주문자 평균 연령
select fo.restaurant_name, 
	   avg(fo.price) as avg_price, 
	   avg(c.age) as avg_age
from food_orders fo
inner join customers c on fo.customer_id = c.customer_id
group by fo.restaurant_name

select restaurant_name,
	   case
	   	when avg_price <= 5000 then '5000 이하'
		when avg_price between 5001 and 10000 then '5000초과'
		when avg_price between 10001 and 30000 then '10000 초과'
		when avg_price > 30000 then '30000 초과'
	   end "평균 주문 금액",	   
	   case
	   	when avg_age < 30 then '20대'
		when avg_age between 30 and 39 then '30대'
		when avg_age between 41 and 49 then '40대'
		when avg_age >50 then '50대 이상'
	   END "평균 연령"
from (
	select fo.restaurant_name, 
		   avg(fo.price) as avg_price, 
		   avg(c.age) as avg_age
	from food_orders fo
	inner join customers c on fo.customer_id = c.customer_id
	group by fo.restaurant_name
) a
order by restaurant_name


select restaurant_name,
       case when price <=5000 then 'price_group1'
            when price >5000 and price <=10000 then 'price_group2'
            when price >10000 and price <=30000 then 'price_group3'
            when price >30000 then 'price_group4' end price_group,
       case when age <30 then 'age_group1'
            when age between 31 and 39 then 'age_group2'
            when age between 40 and 49 then 'age_group3'
            else 'age_group4' end age_group
from
(
select a.restaurant_name,
       avg(price) price,
       avg(age) age
from food_orders a inner join customers b on a.customer_id=b.customer_id
group by 1
) t
order by 1
```
