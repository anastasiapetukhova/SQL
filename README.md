# SQL SELECT

# 📊 SQL Practice - Домашние задания

В рамках обучения мною были выполнены различные SQL-запросы к базе данных MySQL, демонстрирующие владение основными конструкциями языка.

🗂️Инструкция 1. Выведите информацию обо всех продуктах.

📋Решение: SELECT * from products;

🗂️Инструкция 2. Выведите информацию обо всех продуктах, произведенных Apple в категории Phones.

📋Решение: "SELECT * from products
WHERE category = ""phones"" and manufacturer = ""Apple"";"

🗂️Инструкция 3. Выведите названия продуктов и их стоимость, при условии что в названии содержатся буквы sa в любом месте.

📋Решение: "SELECT name, price 
FROM products 
WHERE name LIKE '%sa%';"

🗂️Инструкция 4. Выведите названия продуктов и их стоимость, при условии того, что цена находится в диапазоне от 100 до 1000 долларов.

📋Решение: "SELECT name, price 
FROM products 
WHERE price BETWEEN 100 AND 1000;"

🗂️Инструкция 5. Посчитайте сумму всех товаров, произведенных компанией Samsung. Название таблицы в результате запроса должно быть SAMSUNG TOTAL PRICE.

📋Решение: "SELECT SUM(price) AS 'SAMSUNG TOTAL PRICE'
FROM products 
WHERE manufacturer = 'Samsung';"

🗂️Инструкция 6. Выведите название всех товаров и их стоимость по убыванию.

📋Решение: "SELECT name, price 
FROM products
ORDER BY price DESC;"

🗂️Инструкция 7. Выведите названия всех производителей при условии, чтобы они не повторялись. 

📋Решение: "SELECT DISTINCT manufacturer 
FROM products;"

🗂️Инструкция 8. Выведите названия первых двух категорий продуктов, чтобы они не повторялись.

📋Решение: "SELECT name
FROM products
LIMIT 2;"

🗂️Инструкция 9. Выведите названия продуктов при условии, что они состоят из 12 символов и их названия начинаются с A.

📋Решение: "SELECT name 
FROM products 
WHERE name LIKE 'A%' 
  AND LENGTH(name) = 12;"

🗂️Инструкция 10. Посчитайте среднюю цену всех продуктов. Название таблицы в результате запроса должно быть PRODUCTS AVG PRICE.

📋Решение: "SELECT AVG(price) AS 'PRODUCTS AVG PRICE' 
FROM products;"

🗂️Инструкция 11. Используя оператор IN, выведите названия и описание продуктов, у которых производитель Samsung и Huawei.

📋Решение: "SELECT name, description 
FROM products 
WHERE manufacturer IN ('Samsung', 'Huawei');"

🗂️Инструкция 12. Используя оператор UNION, выведите информацию о названии товаров из таблицы products и номера заказов из таблицы orders.

📋Решение: "SELECT name AS 'Информация'
FROM products

UNION

SELECT order_id AS 'Информация'
FROM orders;"

🗂️Инструкция 13. Используя оператор HAVING, посчитайте количество товаров в каждой категории, оставив только те категории, в которых количество товаров больше 15. 

📋Решение: "SELECT category, COUNT(*) AS product_count
FROM products 
GROUP BY category 
HAVING COUNT(*) > 15;"

🗂️Инструкция 14. "Используя оператор CASE опишите следующую логику:
Выведите компанию, категорию, стоимость и название товара, а также следующий текстовое сообщение:

Если компания Apple, то в консоли должно вывестись ""Это продукт компании Apple"".

Если компания Samsung, то в консоли должно вывестись ""Это продукт компании Samsung"".

Если компания Huawei, то в консоли должно вывестись ""Это продукт компании  Huawei"".

Если компания Xiaomi, то в консоли должно вывестись ""Это продукт компании Xiaomi""."

📋Решение: "SELECT 
    manufacturer AS company,
    category,
    price AS cost,
    name AS product_name,
    CASE 
        WHEN manufacturer = 'Apple' THEN 'Это продукт компании Apple'
        WHEN manufacturer = 'Samsung' THEN 'Это продукт компании Samsung'
        WHEN manufacturer = 'Huawei' THEN 'Это продукт компании Huawei'
        WHEN manufacturer = 'Xiaomi' THEN 'Это продукт компании Xiaomi'
        ELSE 'Это продукт другой компании'
    END AS company_message
FROM products;"
