## Задание 1 – SQL

Ты хочешь посмотреть распределение time-to-convert – отрезка времени (в днях) между заходом на сайт и оформление заказа. 
Target-график выглядит вот так:

![image](https://user-images.githubusercontent.com/91524886/139208524-9218476b-6e4c-4975-b3f8-1aaeadbce1fd.png)

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

## 3. Как поменять запрос, чтобы учитывать только те дни, в которых число заказов превышает 200?
![image](https://user-images.githubusercontent.com/91524886/139208184-949cab86-d9ce-462a-9aaa-fb779ba84587.png)
![image](https://user-images.githubusercontent.com/91524886/139208251-16a3eaca-f89d-4627-88bc-c2768a540d6b.png)

## Задание 2 – План/факт опять не хотят дружить

Перед тобой план / факт график заказов в Сбермаркете. Команда ломает голову по поводу того, что могло пойти не так: почему план и прогноз разошлись так сильно к концу года!

Помоги команде понять, с чем это может быть связано, и предложи гипотезы, которые бы ты проверял в порядке приоритетности.
![image](https://user-images.githubusercontent.com/91524886/139208378-14faec33-3d9d-4c4b-88f3-20701a741529.png)


