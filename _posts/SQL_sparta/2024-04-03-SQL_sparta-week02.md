---
layout: post
title: SQL_sparta - week02
date: 2024-04-03
category: SQL_sparta
---

## week02.sql
```sql
-- 사칙연산 + - * /
select
	food_preparation_time,
	delivery_time,
	food_preparation_time + delivery_time as total_time
from
	food_orders

-- ------------------------------------------------------------
-- 집계함수
-- SUM, AVERAGE, COUNT, MIN, MAX	
select
	sum(food_preparation_time) total_food_preparation_time,
	avg(delivery_time) avg_food_preparation_time
from
	food_orders

select AVG(age) as average_of_age
from customers

-- 번체 행 개수 : 1898 개
select count(1) count_of_orders,
       count(distinct customer_id) count_of_customers
from food_orders

select count(*) total_count, 
       count(DISTINCT pay_type) pay_type
from payments

-- union : 합집합 중복제거
-- union all : 합집합 중복제거 안 함.
select quantity
from food_orders
union SELECT DISTINCT quantity
from food_orders

select quantity
from food_orders
union all SELECT DISTINCT quantity
from food_orders

select min(price) min_price,
       max(price) max_price
from food_orders

SELECT min(quantity) min_quantity, 
       max(quantity) max_quantity
from food_orders

-- 주문 금액이 30,000원 이상인 주문건의 갯수 구하기
select count(*) count_of_orders
from food_orders
where price >= 30000

-- 한국 음식의 주문 당 평균 음식가격 구하기
-- 평균 음식 가격은 price의 평균이다.
SELECT avg(price) average_price
from food_orders
where cuisine_type = 'Korean'

-- ------------------------------------------------------------
-- 범주별 연산 group by
select cuisine_type,
       sum(price) sum_of_price
from food_orders
group by cuisine_type

-- 음식점별 주문 금액 최댓값 조회하기
select restaurant_name, 
       max(price) max_price
from food_orders
group by restaurant_name

-- 결제 타입별 가장 최근 결제일 조회하기
-- date VARCHAR(15)
select pay_type "결제타입", 
       max(date) "최근 결제일"
from payments
group by pay_type

-- -------------------------------------------------------------
-- having절
select restaurant_name, 
       max(price) max_price
from food_orders
group by restaurant_name
having max_price > 25000
order by max_price

-- ------------------------------------------------------------
-- 정렬 order by
-- 오름차순
select cuisine_type,
       sum(price) sum_of_price
from food_orders
group by cuisine_type
order by sum(price)

-- 내림차순
select cuisine_type,
       sum(price) sum_of_price
from food_orders
group by cuisine_type
order by sum(price) desc

-- 음식점별 주문 금액 최댓값 조회하기 - 최댓값 기준으로 내림차순 정렬
select restaurant_name, 
       MAX(price) "최대 주문금액"
from food_orders
group by restaurant_name
order by MAX(price) desc  

-- 고객을 이름 순으로 오름차순으로 정렬하기
-- 필드 순서대로 정렬
-- group by name을 하면 중복된 이름은 한 번만 출력
select *
from customers
order by gender desc, name

-- ------------------------------------------------------------
select cuisine_type, sum(delivery_time) total_delivery_time
from food_orders
where day_of_the_week = 'Weekend'
group by cuisine_type
order by sum(delivery_time) desc

select age, count(name) count_of_name
from customers
where age between 20 and 40
group by age
order by age 

-- -----------------------------------------------------------
-- 음식 종류별 가장 높은 주문 금액과 가장 낮은 주문금액을 조회하고, 가장 낮은 주문금액 순으로 (내림차순) 정렬하기
select cuisine_type, MAX(price), MIN(price)
from food_orders
group by cuisine_type
order by MIN(price) desc
```
