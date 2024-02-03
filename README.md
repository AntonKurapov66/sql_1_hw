# Домашнее задание к занятию "SQL. Часть 1" - `Курапов Антон`


### Задание 1
* Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a” и не содержат пробелов.

   ![alt text](https://github.com/AntonKurapov66/sql_1_hw/blob/main/img/1.PNG)

*  SELECT DISTINCT(district) FROM address WHERE district LIKE "K%a" AND district NOT LIKE "% %";
### Задание 2
* Получите из таблицы платежей за прокат фильмов информацию по платежам, которые выполнялись в промежуток с 15 июня 2005 года по 18 июня 2005 года включительно и стоимость которых превышает 10.00.

  ![alt text](https://github.com/AntonKurapov66/sql_1_hw/blob/main/img/2.PNG)

*  SELECT * FROM payment WHERE payment_date BETWEEN '2005-06-15 00:00:00' AND '2005-06-18 23:59:59' AND amount > 10.00;

### Задание 3
* Получите последние пять аренд фильмов.

  ![alt text](https://github.com/AntonKurapov66/sql_1_hw/blob/main/img/3.PNG)

*  SELECT * FROM rental ORDER BY rental_date DESC LIMIT 5;

### Задание 4
* Одним запросом получите активных покупателей, имена которых Kelly или Willie.
* Сформируйте вывод в результат таким образом:
  *  все буквы в фамилии и имени из верхнего регистра переведите в нижний регистр,
  *  замените буквы 'll' в именах на 'pp'.

 ![alt text](https://github.com/AntonKurapov66/sql_1_hw/blob/main/img/4.PNG)

* SELECT customer_id, store_id, replace(lower(first_name),'ll','pp'), lower(last_name), email, address_id, active, create_date, last_update  FROM customer WHERE first_name IN ('Kelly','Willie') AND active = TRUE;


### Задание 5*
* Выведите Email каждого покупателя, разделив значение Email на две отдельных колонки: в первой колонке должно быть значение, указанное до @, во второй — значение, указанное после @.

  ![alt text](https://github.com/AntonKurapov66/sql_1_hw/blob/main/img/5.PNG)

* SELECT LEFT(email, POSITION('@' IN email)-1) AS email_before_dog, RIGHT(email,LENGTH(email)- POSITION('@' IN email)) AS email_after_dog  FROM customer;

### Задание 6*
* Доработайте запрос из предыдущего задания, скорректируйте значения в новых колонках: первая буква должна быть заглавной, остальные — строчными.

  ![alt text](https://github.com/AntonKurapov66/sql_1_hw/blob/main/img/6.PNG)

* SELECT CONCAT(UPPER(LEFT(email, 1)),LOWER(SUBSTR(LEFT(email, POSITION('@' IN email)-1),2))) AS email_before_dog, RIGHT(email,LENGTH(email)- POSITION('@' IN email)) AS email_after_dog FROM customer;
