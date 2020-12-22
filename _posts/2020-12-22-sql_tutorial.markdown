---
layout: post
title:      "SQL Tutorial"
date:       2020-12-22 15:39:28 -0500
permalink:  sql_tutorial
---

In this tutorial we will cover the main statements use in SQL. First, let's create two tables.

CREATE a(
  id INT,
  column1 VARCHAR
  PRIMARY KEY(id)
)

CREATE TABLE b(
  id INT,
  column1 VARCHAR,
  PRIMARY KEY(id)
)

And insert data into the tables.

INSERT INTO a
VALUES(1,'a','a')

INSERT INTO b
VALUES(1,'a','a')

Now we can select data from a table.

SELECT * FROM a

If we want to remove a table. use the drop statement.

DROP TABLE b

Use a where statement to specify data that we want to extract from a table.

SELECT * FROM a
WHERE column1 = column2

Update a value in a table by using an update statement.

UPDATE a
SET column2='b'
WHERE column1='a'

Delete a value from a table by using a delete statement.

DELETE FROM a 
WHERE column1='a'

Add a column to a table by using the alter statement.

ALTER TABLE a
ADD column3 INT

Select everywhere that a value is in a table with a like statement.

SELECT * FROM a
WHERE id LIKE 'a%'

Use a order by statement to order the table by ASC or DESC.

SELECT * FROM a
ORDER BY id DESC

Use a group by statement to group the data by value.

SELECT * FROM a
group by id

Use a having clause to specify how the data should be grouped.

SELECT * FROM a 
WHERE column1='a'
GROUP BYid
HAVING column2='a'

Join two tables using an inner join to get the data that both tables have in common,

SELECT * FROM a
INNER JOIN b
on a.column1=b.column1

a left join to get the data that both tables have in common and the left tables data,

SELECT * FROM a
LEFT JOIN b
on a.column1=b.column1

or an outer join to get all the data from both tables.

SELECT * FROM a
OUTER JOIN b
on a.column1=b.column1
