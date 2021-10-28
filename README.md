## Задание 1 – SQL

Ты хочешь посмотреть распределение time-to-convert – отрезка времени (в днях) между заходом на сайт и оформление заказа. 
то есть для каждого варианта time_to_convert нужно знать

- количество заказов, которые были совершены в таким time_to_convert
- % заказов от общего числа
- кумулятивный % заказов

У тебя уже есть таблица  `mart_orders` , в которой лежат 

- **main_page_viewed_dt** – дата захода на сайт
- **order_completed_dt** – дата оформления заказа
- **order_id** – уникальный идентификатор заказа

 и часть скрипта:
 with base_table as 
(select date_diff(order_completed_dt, main_page_viewed_dt, day) as time_to_convert
        , count(order_id) as orders
from analytics.mart_orders
where order_completed_dt is not null
group by time_to_convert)

select time_to_convert
        , orders
				, (a) as percent
				, (b) as cumulative_percent
from base_table
order by time_to_convert desc
## 1. Что нужно вставить в (a)? (percent)

1. orders/sum(orders) over() 
2. orders/sum(orders) over(order by time_to_convert) 
3. orders/sum(orders)

## 2. Что нужно вставить в (b) (cumulative_percent)

1. sum(orders) over(order by time_to_convert) / sum(orders) over()
2. sum(orders) over(order by time_to_convert) / sum(orders) 
3. sum(orders) over(partition by time_to_convert order by time_to_convert) / sum(orders) ****
