# mysql-1
# Домашнее задание к занятию «SQL. Часть 1»


## Задание 1
Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a” и не содержат пробелов.

  SELECT DISTINCT a.district 
  FROM address a 
  WHERE district NOT LIKE '% %' 
  AND district LIKE 'K%'
  AND district LIKE '%a';

## Задание 2
Получите из таблицы платежей за прокат фильмов информацию по платежам, которые выполнялись в промежуток с 15 июня 2005 года по 18 июня 2005 года включительно и стоимость которых превышает 10.00.
  
  SELECT p.payment_date  
  FROM payment p 
  WHERE CAST(p.payment_date AS DATE)
  BETWEEN '2005-06-15' AND '2005-06-18' 
  ORDER BY p.payment_date ;

## Задание 3
Получите последние пять аренд фильмов.

  SELECT * FROM rental
  ORDER BY rental_date DESC
  LIMIT 5;

## Задание 4

Одним запросом получите активных покупателей, имена которых Kelly или Willie.

Сформируйте вывод в результат таким образом:

Все буквы в фамилии и имени из верхнего регистра переведите в нижний регистр,
    замените буквы 'll' в именах на 'pp'.

  SELECT REPLACE(LOWER(c.last_name),'ll','pp'), 
  LOWER(c.last_name)
  FROM customer c
  WHERE c.active = '1';

## Задание 5*

Выведите Email каждого покупателя, разделив значение Email на две отдельных колонки: в первой колонке должно быть значение, указанное до @, во второй — значение, указанное после @.

  SELECT
  LEFT(email, LOCATE('@',email)-1),
  SUBSTR(email,LOCATE('@',email) + 1)
  FROM customer c ;

