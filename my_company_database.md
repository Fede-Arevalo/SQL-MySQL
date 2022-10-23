mysql> CREATE DATABASE my_company_database;

mysql> USE my_company_database;
Database changed
mysql> CREATE TABLE employees(
    -> id INT AUTO_INCREMENT,
    -> birth_date DATETIME,
    -> first_name VARCHAR(100),
    -> last_name VARCHAR(100),
    -> gender VARCHAR(100),
    -> PRIMARY KEY(id)
    -> );

mysql> ALTER TABLE employees ADD salary FLOAT;

mysql> ALTER TABLE employees ADD title VARCHAR(100);

mysql> ALTER TABLE employees ADD title_date DATE;

mysql> ALTER TABLE employees MODIFY COLUMN birth_date DATE;

mysql> INSERT INTO employees 
(first_name, last_name, birth_date, gender, title, title_date, salary) values 
("Federico", "Arevalo", "1988-05-18", "Hombre", "Full Stack Developer", "2023-01-27", "5000");

mysql> INSERT INTO employees 
(first_name, last_name, birth_date, gender, title, title_date, salary) values 
("Federico", "Arevalo", "1988-05-18", "Hombre", "Full Stack Developer", "2023-01-27", "5000");

mysql> DELETE FROM employees WHERE id = 2;

mysql> INSERT INTO employees 
(first_name, last_name, birth_date, gender, title, title_date, salary) values 
("Federico", "Perez", "1985-02-21", "Hombre", "Ingeniero Civil", "2003-01-02", "6000"), 
("Federico", "Rinaudo", "1983-12-21", "Hombre", "Ingeniero Electronico", "2019-01-02", "8000"), 
("Elisa", "Baugini", "1989-06-17", "Mujer", "Medico", "2010-01-02", "7000"), 
("Laura", "Puentes", "1990-03-09", "Mujer", "Contadora", "2020-01-02", "6500"), 
("Maite", "Cequini", "1991-09-19", "Mujer", "Traductora de Ingles", "2020-05-22", "7500"), 
("Nora", "Puentes", "1980-03-09", "Mujer", "Costurera", "2005-05-02", "6900"), 
("Martin", "Mengod", "1990-12-09", "Hombre", "Arquitecto", "2020-01-02", "19500"), 
("Nicasio", "Oroño", "1992-02-15", "Hombre", "Paisajista", "2020-06-20", "29600"), 
("Maria", "Carey", "1993-10-09", "Mujer", "Cantante", "2021-01-02", "25600"), 
("Ursula", "Corbero", "1994-12-09", "Mujer", "Actriz", "2020-01-02", "19500"),
("Ernesto", "Cheguevara", "1980-05-11", "Hombre", "Rebelde", "2000-01-02", "50000"), 
("Diego", "Maradona", "1983-03-03", "Hombre", "Futbolista", "2000-01-02", "40000"), 
("Tash", "Sultana", "1995-06-07", "Mujer", "Cantante", "2010-01-02", "30000"), 
("Sara", "Williams", "1990-08-19", "Mujer", "Administrativa", "2020-01-02", "26500"), 
("Ricardo", "Ponce", "1992-10-28", "Hombre", "Sanador", "2018-05-22", "17500");

UPDATE employees SET first_name="Eurialio" WHERE first_name="Ricardo" AND last_name="Ponce" AND birth_date="1992-10-28";

SELECT * FROM employees WHERE salary>20000;
+----+------------+------------+------------+--------+--------+----------------+------------+
| id | birth_date | first_name | last_name  | gender | salary | title          | title_date |
+----+------------+------------+------------+--------+--------+----------------+------------+
| 10 | 1992-02-15 | Nicasio    | Oroño      | Hombre |  29600 | Paisajista     | 2020-06-20 |
| 11 | 1993-10-09 | Maria      | Carey      | Mujer  |  25600 | Cantante       | 2021-01-02 |
| 13 | 1980-05-11 | Ernesto    | Cheguevara | Hombre |  50000 | Rebelde        | 2000-01-02 |
| 14 | 1983-03-03 | Diego      | Maradona   | Hombre |  40000 | Futbolista     | 2000-01-02 |
| 15 | 1995-06-07 | Tash       | Sultana    | Mujer  |  30000 | Cantante       | 2010-01-02 |
| 16 | 1990-08-19 | Sara       | Williams   | Mujer  |  26500 | Administrativa | 2020-01-02 |
+----+------------+------------+------------+--------+--------+----------------+------------+

SELECT * FROM employees WHERE salary<10000;
+----+------------+------------+-----------+--------+--------+-----------------------+------------+
| id | birth_date | first_name | last_name | gender | salary | title                 | title_date |
+----+------------+------------+-----------+--------+--------+-----------------------+------------+
|  1 | 1988-05-18 | Federico   | Arevalo   | Hombre |   5000 | Full Stack Developer  | 2023-01-27 |
|  3 | 1985-02-21 | Federico   | Perez     | Hombre |   6000 | Ingeniero Civil       | 2003-01-02 |
|  4 | 1983-12-21 | Federico   | Rinaudo   | Hombre |   8000 | Ingeniero Electronico | 2019-01-02 |
|  5 | 1989-06-17 | Elisa      | Baugini   | Mujer  |   7000 | Medico                | 2010-01-02 |
|  6 | 1990-03-09 | Laura      | Puentes   | Mujer  |   6500 | Contadora             | 2020-01-02 |
|  7 | 1991-09-19 | Maite      | Cequini   | Mujer  |   7500 | Traductora de Ingles  | 2020-05-22 |
|  8 | 1980-03-09 | Nora       | Puentes   | Mujer  |   6900 | Costurera             | 2005-05-02 |
+----+------------+------------+-----------+--------+--------+-----------------------+------------+

SELECT * FROM employees WHERE salary BETWEEN 14000 AND 50000;
+----+------------+------------+------------+--------+--------+----------------+------------+
| id | birth_date | first_name | last_name  | gender | salary | title          | title_date |
+----+------------+------------+------------+--------+--------+----------------+------------+
|  9 | 1990-12-09 | Martin     | Mengod     | Hombre |  19500 | Arquitecto     | 2020-01-02 |
| 10 | 1992-02-15 | Nicasio    | Oroño      | Hombre |  29600 | Paisajista     | 2020-06-20 |
| 11 | 1993-10-09 | Maria      | Carey      | Mujer  |  25600 | Cantante       | 2021-01-02 |
| 12 | 1994-12-09 | Ursula     | Corbero    | Mujer  |  19500 | Actriz         | 2020-01-02 |
| 13 | 1980-05-11 | Ernesto    | Cheguevara | Hombre |  50000 | Rebelde        | 2000-01-02 |
| 14 | 1983-03-03 | Diego      | Maradona   | Hombre |  40000 | Futbolista     | 2000-01-02 |
| 15 | 1995-06-07 | Tash       | Sultana    | Mujer  |  30000 | Cantante       | 2010-01-02 |
| 16 | 1990-08-19 | Sara       | Williams   | Mujer  |  26500 | Administrativa | 2020-01-02 |
| 17 | 1992-10-28 | Eurialio   | Ponce      | Hombre |  17500 | Sanador        | 2018-05-22 |
+----+------------+------------+------------+--------+--------+----------------+------------+ 

SELECT COUNT(*) FROM employees;
+----------+
| COUNT(*) |
+----------+
|       16 |
+----------+

 SELECT * FROM employees WHERE YEAR(title_date)=2019;
+----+------------+------------+-----------+--------+--------+-----------------------+------------+
| id | birth_date | first_name | last_name | gender | salary | title                 | title_date |
+----+------------+------------+-----------+--------+--------+-----------------------+------------+
|  4 | 1983-12-21 | Federico   | Rinaudo   | Hombre |   8000 | Ingeniero Electronico | 2019-01-02 |
+----+------------+------------+-----------+--------+--------+-----------------------+------------+

SELECT UPPER(first_name) FROM employees;
+-------------------+
| UPPER(first_name) |
+-------------------+
| FEDERICO          |
| FEDERICO          |
| FEDERICO          |
| ELISA             |
| LAURA             |
| MAITE             |
| NORA              |
| MARTIN            |
| NICASIO           |
| MARIA             |
| URSULA            |
| ERNESTO           |
| DIEGO             |
| TASH              |
| SARA              |
| EURIALIO          |
+-------------------+

SELECT DISTINCT first_name FROM employees;
+------------+
| first_name |
+------------+
| Federico   |
| Elisa      |
| Laura      |
| Maite      |
| Nora       |
| Martin     |
| Nicasio    |
| Maria      |
| Ursula     |
| Ernesto    |
| Diego      |
| Tash       |
| Sara       |
| Eurialio   |
+------------+

DELETE FROM employees WHERE id=5;

DELETE FROM employees WHERE salary>20000;



// Final table:

SELECT * FROM employees;
+----+------------+------------+-----------+--------+--------+-----------------------+------------+
| id | birth_date | first_name | last_name | gender | salary | title                 | title_date |
+----+------------+------------+-----------+--------+--------+-----------------------+------------+
|  1 | 1988-05-18 | Federico   | Arevalo   | Hombre |   5000 | Full Stack Developer  | 2023-01-27 |
|  3 | 1985-02-21 | Federico   | Perez     | Hombre |   6000 | Ingeniero Civil       | 2003-01-02 |
|  4 | 1983-12-21 | Federico   | Rinaudo   | Hombre |   8000 | Ingeniero Electronico | 2019-01-02 |
|  6 | 1990-03-09 | Laura      | Puentes   | Mujer  |   6500 | Contadora             | 2020-01-02 |
|  7 | 1991-09-19 | Maite      | Cequini   | Mujer  |   7500 | Traductora de Ingles  | 2020-05-22 |
|  8 | 1980-03-09 | Nora       | Puentes   | Mujer  |   6900 | Costurera             | 2005-05-02 |
|  9 | 1990-12-09 | Martin     | Mengod    | Hombre |  19500 | Arquitecto            | 2020-01-02 |
| 12 | 1994-12-09 | Ursula     | Corbero   | Mujer  |  19500 | Actriz                | 2020-01-02 |
| 17 | 1992-10-28 | Eurialio   | Ponce     | Hombre |  17500 | Sanador               | 2018-05-22 |
+----+------------+------------+-----------+--------+--------+-----------------------+------------+

