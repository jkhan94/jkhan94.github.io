---
layout: post
title: SQL_sparta - week01
date: 2024-04-02
category: WebRookie_sparta
---

## week01.sql
```sql
-- select + from 테이블명
-- 테이블의 모든 행 출력
select *
from food_orders

select *
from payments 

select *
from customers


-- select 컬럼1, 컬럼2 from 테이블
-- 명시한 열 데이터만 출력
select order_id, restaurant_name
from food_orders

-- ---------------------------------------------------
-- 컬럼 별명 붙이기 alias
-- 방법1 : 컬럼1 as 별명1
-- 방법2 : 컬럼2 "별명2"
select order_id as ord_no, restaurant_name "식당 이름"
from food_orders

SELECT order_id ord_no, price "가격", quantity as "수량"
from food_orders
	
select name "이름", email "e-mail"
from customers

-- ---------------------------------------------------
-- where절 필터링
select *
from customers
where age = 21
and gender = 'female'

SELECT *
from food_orders
where cuisine_type = 'Korean'

select *
from payments
where pay_type = 'card'

-- 비교연산: =, <>, >, >=, <, <=
select *
from customers
where age<21 and gender <>'male'

select *
from customers
where age >= 40

select *
from food_orders
where price < 15000

-- between
select *
from customers
where age between 10 and 20

select *
from food_orders
where price between 20000 and 30000

-- in (... , ... , ... )
select *
from customers
where age in (15, 21, 31)

SELECT *
from food_orders
where cuisine_type in ('Korean', 'Japanese')

-- like '%'
select *
from customers
where name like '김%'

select *
from food_orders
where restaurant_name like 'B%'

SELECT *
from food_orders
where restaurant_name like '%Next%'

select *
from customers
where name like '%아'

-- ---------------------------------------------------
-- 논리연산
-- and, or, not
select *
from customers
where age >= 21
and gender = 'male'

select *
from food_orders
where cuisine_type = 'Korean'
and price >= 30000

select *
from payments
where pay_type = 'card'
or vat <= 0.2

select *
from payments
where not pay_type = 'cash'
and vat <= 0.2

-- ---------------------------------------------------
-- 숙제: 상품 준비시간이 20~30분 사이인, 한국음식점의 식당명과 고객번호 조회하기
select restaurant_name, customer_id
from food_orders
where cuisine_type = 'Korean'
and food_preparation_time between 20 and 30

select restaurant_name, customer_id
from food_orders
where cuisine_type = 'Korean'
and 20 <= food_preparation_time
and food_preparation_time <= 30

```
