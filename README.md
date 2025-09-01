# Домашнее задание к занятию "`Работа с данными (DDL/DML)`" - `Лоскутов Вячеслав`

---

### Задание 1

1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.
1.2. Создайте учётную запись sys_temp.
1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)
1.4. Дайте все права для пользователя sys_temp.
1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)
1.6. Переподключитесь к базе данных от имени sys_temp.

Для смены типа аутентификации с sha2 используйте запрос:
ALTER USER 'sys_test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

1.6. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.
1.7. Восстановите дамп в базу данных.
1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)

Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.

### Ответ:

Устанавливаем и включаем MySQL сервер на локальной виртуальной машине:
```
sudo apt install mysql-server -y;
sudo systemctl start mysql;
sudo systemctl enable mysql.
```
Подключаемся к MySQL, создаём учётную запись sys_temp и запрашиваем список пользователей:
```
sudo mysql -u root -p;
CREATE USER 'sys_temp'@'localhost' IDENTIFIED BY 'password';
SELECT User, Host FROM mysql.user;
```
![users](https://github.com/NightWalkerZ488/hw-ddl/blob/main/users1.PNG)

Даём все права sys_temp и запрашиваем список прав:
```
GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'localhost' WITH GRANT OPTION;
SHOW GRANTS FOR 'sys_temp'@'localhost';
```
![privilegs](https://github.com/NightWalkerZ488/hw-ddl/blob/main/privilegs.PNG)

Подключаемся к базе от имени sys_tmp:

```
exit;
mysql -u sys_temp -p.
```
Восстанавливаем скачанный дамп базы данных и смотри список таблиц:

```
CREATE DATABASE sakila CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
mysql -u sys_temp -p sakila < sakila-schema.sql;
mysql -u sys_temp -p sakila < sakila-schema.sql;
mysql -u sys_temp -p sakila;
SHOW TABLES.
```
Список таблиц:

[tables](https://github.com/NightWalkerZ488/hw-ddl/blob/main/sakila_tables.PNG)


### Задание 2

Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)

Название таблицы | Название первичного ключа
customer         | customer_id

### Ответ:

