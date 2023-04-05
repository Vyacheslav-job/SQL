### My SQL Queries

#### Создание таблицы

CREATE TABLE book(
  book_id INT PRIMARY KEY AUTO_INCREMENT,
  title VARCHAR(50),
  author VARCHAR(30),
  price DECIMAL(8, 2),
  amount INT
)

#### Добавление записей в таблицу

INSERT INTO book (title, author, price, amount) VALUES ('Мастер и Маргарита', 'Булгаков М.А.', 670.99, 3)
INSERT INTO book (title, author, price, amount) VALUES ('Белая гвардия', 'Булгаков М.А.', 540.50, 5);
INSERT INTO book (title, author, price, amount) VALUES ('Идиот', 'Достоевский Ф.М.', 460.00, 10);
INSERT INTO book (title, author, price, amount) VALUES ('Братья Карамазовы', 'Достоевский Ф.М.', 799.01, 2);


#### Выборка отдельных столбцов

SELECT author, title, price FROM book


#### Выборка новых столбцов и присвоение им новых имен

SELECT title AS Название, author AS Автор FROM book


#### Выборка данных с созданием вычисляемого столбца

SELECT title, amount,
    amount * 1.65 AS pack
FROM book

SELECT title, author, amount,
    ROUND((price * 0.7), 2) AS new_price
FROM book

SELECT author, title, 
    ROUND(IF(author = 'Булгаков М.А.', price * 1.1, IF(author = 'Есенин С.А.', price * 1.05, price * 1)), 2) AS  new_price
FROM book


#### Выборка данных по условию

SELECT author, title, price
FROM book
WHERE amount < 10

SELECT title, author, price, amount
FROM book
WHERE (price < 500 OR price > 600) AND price * amount >= 5000

SELECT title, author
FROM book
WHERE (price BETWEEN 540.50 AND 800) AND (amount IN (2, 3, 5, 7))

SELECT author, title
FROM book
WHERE amount BETWEEN 2 AND 14
ORDER BY author DESC, title

SELECT title, author FROM book
WHERE title LIKE "%_ _%" AND author LIKE "%С.%" 
ORDER BY title

SELECT title, author FROM book
WHERE author LIKE "Б%"
ORDER BY title 


