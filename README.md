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
![image](https://user-images.githubusercontent.com/91524886/139208034-4c41618e-bfb6-4a99-8920-b4f99afd2e24.png)
## 1. Что нужно вставить в (a)? (percent)

1. orders/sum(orders) over() 
2. orders/sum(orders) over(order by time_to_convert) 
3. orders/sum(orders)

## 2. Что нужно вставить в (b) (cumulative_percent)

1. sum(orders) over(order by time_to_convert) / sum(orders) over()
2. sum(orders) over(order by time_to_convert) / sum(orders) 
3. sum(orders) over(partition by time_to_convert order by time_to_convert) / sum(orders) ****
