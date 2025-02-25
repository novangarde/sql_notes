
>Что концептуально представляют собой атрибуты сущности ER-модели?
>	Характеристики сущностей

> Язык описания логических моделей данных:
> 	SQL

> Понятие связей между сущностями
> 	Внешний ключ

> Первая нормальная форма (1NF) это
> 	В каждой ячейки одно значение

> Первичный ключ это
> 	Уникальный идентификатор записи в таблице

> Что если CHECK CONSTRAINT не пройдет
> 	Операция будет отклонена

> DDL для создания CHECK CONSTRAINT
> 	ALTER TABLE

> Создать FOREIGN KEY
> 	ADD CONSTRAINT

> Как создать составной ключ
> 	CREATE INDEX index_name ON table (column1, column2)

> Что делает COMMIT
> 	Подтверждает транзакцию

> Реляционная БД это
> 	Структура основанная на связях

> НЕ реляционная БД
> 	MongoDB

> Служба доступа к данным
> 	DBMS

> CAP
> 	consistency availably partition tolerance

> Какой принцип ACID гарантирует, что если транзакция прошла успешно, изменения будут сохранены даже в случае сбоя системы?
> 	durability (Надежность)

> Что вернет запрос: SELECT 1+1 WHERE 1=1 AND 1=2
> 	ничего, потому что **Условие `1=1 AND 1=2` всегда будет ложным, так как `1=2` всегда неверно.**

> Что вернет запрос: select * from hobby where student id =1 and student id=3
> 	ничего, т.к. and на один и тот же столбец, **но при этом запрашиваются два взаимоисключающих условия**

> Что вернет запрос select sum(t1.value) from (select null::integer as value) as t1
> 	null, **потому что во вложенном запросе выбирается null::integer as value, соответственно, при возврате value возвращается null**

> Что вернет запрос select count(*) from student as s where exists(select null from hobby as h where h.student_id = s.id limit 1)
> 	2, **потому что 1. Подзапрос: `SELECT NULL FROM Hobby AS h WHERE h.student_id = s.id LIMIT 1` проверяет, есть ли запись в таблице `Hobby` для каждого студента из таблицы `Student`. Если такая запись найдена, подзапрос возвращает `NULL`, но это не важно, так как `EXISTS` проверяет только наличие строки, а не ее содержимое. Кстати, LIMIT 1: Это необязательно, так как `EXISTS` прекращает выполнение подзапроса сразу после нахождения первой строки. Однако `LIMIT 1` явно указывает, что достаточно найти одну строку.**

> Что вернет запрос select count(*) from student as s where id in (select * from hobby)
> 	Syntax Error, **потому что 1. *_SELECT _:__ Подзапрос `SELECT * FROM Hobby` возвращает все колонки таблицы `Hobby`. Если в таблице `Hobby` несколько колонок, это может вызвать ошибку, так как `IN` ожидает список значений одного типа, а не набор кортежей.**

> Что вернет запрос SELECT reg_num FROM Student ORDER BY NULLS LAST LIMIT 1;
> 	123

> select student from student group by student having student like ‘%Анна%’ limit 1
> 	‘Анна’

> select distinct employee as emp from employee order by 1 desc limit 1
> 	Ирина

> SELECT employee FROM ( SELECT employee, row_number() OVER (ORDER BY transaction) AS row_num FROM employee GROUP BY employee) AS t1 WHERE t1.row num = 2 ORDER BY 1 ASC LIMIT 1
> 	Анна

> select employee, sum(transaction) from employee group by employee order by 2 desc limit 1
> 	Иван, 430

>SELECT string_add(t1.id::VARCHAR,','ORDER BY t1.id) AS result FROM ( SELECT s.id FROM Student AS s UNION SELECT h.student_id FROM Hobby AS h) AS t1
>	1,2,3,4

> Какое количество строк и столбцов получится после запроса SELECT * FROM Student as s CROSS JOIN Hobby AS h
> 	r = 12, c = 5

