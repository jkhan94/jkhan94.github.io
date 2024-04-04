---
layout: post
title: SQL_sparta - week03
date: 2024-04-04
category: SQL_sparta
---

## week03.sql
```sql
-- replace(바꿀 컬럼, 현재 값, 바꿀 값)
-- 문자 변경

-- 식당 명의 ‘Blue Ribbon’ 을 ‘Pink Ribbon’ 으로 바꾸기
select restaurant_name "원래 상점명",
       replace(restaurant_name, 'Blue', 'Pink') "바뀐 상점명"
from food_orders
where restaurant_name like '%Blue Ribbon%'

-- 주소의 ‘문곡리’ 를 ‘문가리’ 로 바꾸기
select addr "원래 주소", 
       REPLACE(addr, '문곡리', '문가리')  "바뀐 주소"
from food_orders
where addr like '%문곡리%'

-- -----------------------------------------------------------
-- substr(조회 할 컬럼, 시작 위치, 읽을 글자 수)
-- 특정 문자만 골라서 조회.

-- 서울 음식점들의 주소를 전체가 아닌 ‘시도’ 만 나오도록 수정
select addr "원래 주소", 
       substr(addr, 1, 2) "시도"
from food_orders
where addr like '%서울특별시%'

-- 공백, 구의 첫 글자 출력
select addr "원래 주소", 
       substring(addr, 6, 2) "시도"
from food_orders
where addr like '%서울특별시%'

-- -----------------------------------------------------------
-- concat(붙이고 싶은 값1, 붙이고 싶은 값2, 붙이고 싶은 값3, .....)
-- 여러 컬럼의 값을 하나로 합치기

-- 서울시에 있는 음식점은 ‘[서울] 음식점명’ 이라고 수정
select restaurant_name "원래 이름",   
       addr "원래 주소",       
       concat('[', substring(addr, 1, 2), '] ', restaurant_name) "바뀐 이름",
       CONCAT(restaurant_name, ' - ', cuisine_type) "음식 타입별 음식점" 
from food_orders
where addr like '%서울%'

-- -----------------------------------------------------------
-- 서울 지역의 음식 타입별 평균 음식 주문금액 구하기 (출력 : ‘서울’, ‘타입’, ‘평균 금액’) 
-- group by 1, 2: select절에 있는 1, 2번째 컬럼. 지역, 음식타입 순으로 정렬.
select SUBSTRING(addr, 1, 2) "시도", cuisine_type "타입", avg(price) "평균 금액"
from food_orders
where addr like '서울%'
group by 1, 2

-- 이메일 도메인별 고객 수와 평균 연령 구하기
-- locate(찾을 문자, 문자열)
select LOCATE('@','aaaa@naver.com')

SELECT SUBSTR(email, locate('@', email)+ 1) "도메인", 
       count(customer_id) "고객 수", 
       avg(age) "평균 연령"
from customers
group by 1

select substring(email, 10) "이메일 도메인",
       count(customer_id) "고객 수",
       avg(age) "평균 연령"
from customers
group by 1

-- ‘[지역(시도)] 음식점이름 (음식종류)’ 컬럼을 만들고, 총 주문건수 구하기
-- 주문 건수는 개수를 세는 것.
select concat('[', left(addr, 2), '] ', restaurant_name, ' (', cuisine_type, ')') "음식점",
       count(1) "총 주문건수"
from food_orders
group by 1

-- -----------------------------------------------------------
-- 조건문 IF
-- if(조건, 조건을 충족할 때, 조건을 충족하지 못할 때)

-- 음식 타입을 ‘Korean’ 일 때는 ‘한식’, ‘Korean’ 이 아닌 경우에는 ‘기타’ 라고 지정
select restaurant_name,
       cuisine_type "원래 음식 타입",
       if(cuisine_type='Korean', '한식', '기타') "음식 타입"
from food_orders

-- ‘문곡리’ 가 평택에만 해당될 때, 평택 ‘문곡리’ 만 ‘문가리’ 로 수정
select addr, 
       if(locate('평택',addr)<>0, REPLACE(addr, '문곡리', '문가리'),addr)
from food_orders
where addr like '%문곡리%'

select addr "원래 주소",
       if(addr like '%평택군%', replace(addr, '문곡리', '문가리'), addr) "바뀐 주소"
from food_orders
where addr like '%문곡리%'

/* 잘못된 이메일 주소 (gmail) 만 수정을 해서 사용 */
-- 위치 및 도메인 확인
select locate('gmail','aaagmail.com')

select CONCAT(
left('aaagmail.com', locate('gmail', 'aaagmail.com')-1 ), '@', right('aaagmail.com', LENGTH('aaagmail.com')- locate('gmail', 'aaagmail.com')+ 1))

SELECT SUBSTR(if(locate('@', 'aaagmail.com')= 0, REPLACE('aaagmail.com', 'aaagmail.com', CONCAT(left('aaagmail.com', locate('gmail', 'aaagmail.com')-1 ), '@', right('aaagmail.com', LENGTH('aaagmail.com')- locate('gmail', 'aaagmail.com')+ 1))), 'aaagmail.com' ), locate('@', 'aaa@gmail.com')+ 1)

-- @ 넣기
select email "수정 전 이메일", 
if(locate('@', email)= 0, 
   REPLACE(email, email, 
   CONCAT(left(email, locate('gmail', email)-1 ), '@', right(email, LENGTH(email)- locate('gmail', email)+ 1))
   ), email ) "수정 후 이메일"
from customers
where email like '%gmail%'

-- 도메인만 출력
select email "수정 전 이메일", 
	   SUBSTR( if(locate('@', email)= 0, 
	           	  REPLACE(email, email, CONCAT(left(email, locate('gmail', email)-1 ), '@', right(email, LENGTH(email)- locate('gmail', email)+ 1))), 
	           	  email ), 
	           locate('@', 
	           		   if(locate('@', email)= 0, 
	           		  	  REPLACE(email, email, CONCAT(left(email, locate('gmail', email)-1 ), '@', right(email, LENGTH(email)- locate('gmail', email)+ 1))), 
	           		   	  email )
	           		  )+ 1
   		 	  ) "수정 후 이메일"
from customers

-- 최종본
select SUBSTR( 
		if(locate('@', email)= 0, 
		   REPLACE(email, 
			       email, 
				   CONCAT(left(email, locate('gmail', email)-1 ), '@', right(email, LENGTH(email)- locate('gmail', email)+ 1))), 
		   email), 
	   locate('@', 
	   		  if(locate('@', email)= 0, 
	   		  	 REPLACE(email, 
	   		  	 		 email, 
	   		  	 		 CONCAT(left(email, locate('gmail', email)-1 ), '@', right(email, LENGTH(email)- locate('gmail', email)+ 1))), email ))+ 1) "수정 후 이메일", 
	   count(customer_id) "고객 수", 
	   avg(age) "평균 연령"
from customers
group by 1

-- email의 처음부터 10개를 자름.
select substring(if(email like '%gmail%', replace(email, 'gmail', '@gmail'), email), 
                 10) "이메일 도메인",
        count(customer_id) "고객 수", 
        avg(age) "평균 연령"
from customers
group by 1

-- substring 읽어오는 개수 수정
-- 이메일 고치는 쿼리
select customer_id, age,
	   if(email like '%gmail%', replace(email, 'gmail', '@gmail'), email) as fixed_email
from customers
group by 3

-- 고친 이메일로부터 도메인 읽는 쿼리
SELECT right(fixed_email, locate('@', fixed_email)) "이메일 도메인",
	   count(customer_id) "고객 수", 
       avg(age) "평균 연령"
from (
		select customer_id, age,
			   if(email like '%gmail%', replace(email, 'gmail', '@gmail'), email) as fixed_email
		from customers
		group by 3
) a
group by 1

-- -----------------------------------------------------------
-- Case문
/*case when 조건1 then 값(수식)1
     when 조건2 then 값(수식)2
     else 값(수식)3
end*/

-- 음식 타입을 ‘Korean’ 일 때는 ‘한식’, ‘Japanese’ 혹은 ‘Chienese’ 일 때는 ‘아시아’, 그 외에는 ‘기타’ 라고 지정
SELECT case when cuisine_type = 'Korean' then '한식'
			when cuisine_type in ('Japanese', 'Chinese') then '아시아'
			ELSE '기타'
			end "음식타입",
		cuisine_type 
from food_orders

-- 위 코드와 동일.
select restaurant_name,
       cuisine_type "원래 음식 타입",
       if(cuisine_type='Korean', '한식', '기타') "음식 타입"
from food_orders

-- 음식 단가를 주문 수량이 1일 때는 음식 가격, 주문 수량이 2개 이상일 때는 음식가격/주문수량 으로 지정
select order_id, price, quantity,
		case when quantity = 1 then price
			 else price / quantity
		end "음식 단가"
from food_orders

select order_id,
       price,
       quantity,
       case when quantity=1 then price
            when quantity>=2 then price/quantity end "음식 단가"
from food_orders

-- 주소의 시도를 ‘경기도’ 일때는 ‘경기도’, ‘특별시’ 혹은 ‘광역시’ 일 때는 붙여서, 아닐 때는 앞의 두 글자만 사용
select CASE when addr like '%경기도%' then '경기도'
			WHEN addr like '%특별시%' or addr like '%광역시%' then substring(addr, 1, locate(' ', addr)) 
			else substring(addr, 1, 2)	
		END "주소"
from food_orders

select restaurant_name,
       addr,
       case when addr like '%경기도%' then '경기도'
            when addr like '%특별%' or addr like '%광역%' then substring(addr, 1, 5)
            else substring(addr, 1, 2) end "변경된 주소"
from food_orders

-- -----------------------------------------------------------
-- User Segmentation (분류, 새로운 카테고리 만들기)

-- 10세 이상, 30세 미만의 고객의 나이와 성별로 그룹 나누기 (이름도 같이 출력)
-- case는 하나의 열 생성. 이 열을 카테고리로 보는 듯.
-- 조건은 where로 지정.
select name,
       age,
       gender,
       case when (age between 10 and 19) and gender='male' then "10대 남자"
            when (age between 10 and 19) and gender='female' then "10대 여자"
            when (age between 20 and 29) and gender='male' then "20대 남자"
            when (age between 20 and 29) and gender='female' then "20대 여자" end "그룹" 
from customers
where age between 10 and 29

/*
음식 단가, 음식 종류 별로 음식점 그룹 나누기 
(Korean = 한식
Japanese, Chinese, Thai, Vietnamese, Indian = 아시아식
그외 = 기타)
(단가 = 5000, 15000, 그 이상)
*/
select restaurant_name,
       price/quantity "단가",
       cuisine_type,
       order_id,
       case when (price/quantity <5000) and cuisine_type='Korean' then '한식1'
            when (price/quantity between 5000 and 15000) and cuisine_type='Korean' then '한식2'
            when (price/quantity > 15000) and cuisine_type='Korean' then '한식3'
            
            when (price/quantity <5000) and cuisine_type in ('Japanese', 'Chinese', 'Thai', 'Vietnamese', 'Indian') then '아시아식1'
            when (price/quantity between 5000 and 15000) and cuisine_type in ('Japanese', 'Chinese', 'Thai', 'Vietnamese', 'Indian') then '아시아식2'
            when (price/quantity > 15000) and cuisine_type in ('Japanese', 'Chinese', 'Thai', 'Vietnamese', 'Indian') then '아시아식3'
            
            when (price/quantity <5000) and cuisine_type not in ('Korean', 'Japanese', 'Chinese', 'Thai', 'Vietnamese', 'Indian') then '기타1'
            when (price/quantity between 5000 and 15000) and cuisine_type not in ('Korean', 'Japanese', 'Chinese', 'Thai', 'Vietnamese', 'Indian') then '기타2'
            when (price/quantity > 15000) and cuisine_type not in ('Korean', 'Japanese', 'Chinese', 'Thai', 'Vietnamese', 'Indian') then '기타3' end "식당 그룹"
from food_orders

/*
지역과 배달시간을 기반으로 배달수수료 구하기 (식당 이름, 주문 번호 함께 출력)
(지역 : 서울, 기타 - 서울일 때는 수수료 계산 * 1.1, 기타일 때는 곱하는 값 없음
 시간 : 25분, 30분 - 25분 초과하면 음식 가격의 5%, 30분 초과하면 음식 가격의 10%)
*/
select order_id, 
	   restaurant_name, 
	   substring(addr, 1,2) "지역", 
	   delivery_time "배달시간",
	   CASE when addr like '%서울%' and delivery_time >30 then price*0.1*1.1
	   		when addr like '%서울%' and delivery_time >25 then price*0.05*1.1
	   		when addr like '%서울%' and delivery_time >0 then 0
	   		when addr not like '%서울%' and delivery_time >30 then price*0.1
	   		when addr not like '%서울%' and delivery_time >25 then price*0.05
	   		when addr not like '%서울%' and delivery_time >0 then 0
	   END "배달수수료"
from food_orders

select order_id, 
	   restaurant_name, 
	   price,
	   delivery_time,
	   addr,
		case when delivery_time > 30 then price*0.1*if(addr like '%서울%', 1.1, 1)
			when delivery_time between 26 and 29 then price*0.05*if(addr like '%서울%', 1.1, 1)			else 0
		end "수수료"
from food_orders

-- 수수료 포함 가격
select restaurant_name,
       order_id,
       delivery_time,
       price,
       addr,
       case when delivery_time>25 and delivery_time<=30 then price*1.05*(if(addr like '%서울%', 1.1, 1))
            when delivery_time>30 then price*1.1*(if(addr like '%서울%', 1.1, 1))
            else 0 end "수수료 포함 가격"
from food_orders

/*
주문 시기와 음식 수를 기반으로 배달할증료 구하기
(주문 시기 : 평일 기본료 = 3000 / 주말 기본료 = 3500
음식 수 : 3개 이하이면 할증 없음 / 3개 초과이면 기본료 * 1.2)
*/
select order_id, 
	   restaurant_name, 
	   day_of_the_week, 
	   quantity,
	   CASE when day_of_the_week = 'Weekday' then 3000 * if(quantity>3, 1.2, 1)
	   		when day_of_the_week = 'Weekend' then 3500 * if(quantity>3, 1.2, 1)
	   END "배달할증료"
from food_orders

select order_id,
       price,
       quantity,
       day_of_the_week,
       if(day_of_the_week='Weekday', 3000, 3500)*(if(quantity<=3, 1, 1.2)) "할증료"
from food_orders

-- -----------------------------------------------------------
-- 숙제
/*
다음의 조건으로 배달시간이 늦었는지 판단하는 값을 만들어주세요.
주중 : 25분 이상
주말 : 30분 이상
*/
select order_id, restaurant_name, day_of_the_week, delivery_time, 
	CASE when day_of_the_week = 'Weekday' then if(delivery_time >= 25, 'Late', 'On-time')
		 when day_of_the_week = 'Weekend' then if(delivery_time >= 30, 'Late', 'On-time')
	end "지연여부"
from food_orders
```
