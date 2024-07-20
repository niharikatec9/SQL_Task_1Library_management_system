# SQL_Task_1Library_management_system

TASK ONE: LIBRARY MANAGEMENT SYSTEM

<img width="547" alt="retrive" src="https://github.com/user-attachments/assets/82db22f7-05bc-46fc-9482-f96a7fad302a">
<img width="759" alt="members" src="https://github.com/user-attachments/assets/fa9bfd56-da73-4474-8c90-3e4f7c63f6ae">
<img width="690" alt="books" src="https://github.com/user-attachments/assets/9362ea69-e7d2-416f-8565-26e2652e9a6f">

borrow/return transactions. This project helps you learn basic SQL commands
and database design. Design tables for books, members, and transactions.
Write SQL queries to insert, update, delete, and retrieve data.

CREATE TABLE Books (
  BookID INT PRIMARY KEY ,
  Title VARCHAR(255) NOT NULL,
  Author VARCHAR(255) NOT NULL,
  Gener VARCHAR(255),
  PublishedYear INT,
  AvilableCopies INT NOT NULL
 );
  
 CREATE TABLE Members (
   MemberID INT PRIMARY KEY,
   first_name VARCHAR(100) NOT NULL,
   last_name VARCHAR(100) NOT NULL,
   Email VARCHAR(255) UNIQUE NOT NULL,
   Phone_number VARCHAR(20),
   Member_shipdate DATE NOT NULL,
   jion_date Date Not Null
 );
 
 CREATE TABLE Transactions (
   BookID INT PRIMARY KEY,
   MemberID INT,
   BorrowDate DATE NOT NULL,
   ReturunDate DATE,
   FOREIGN KEY (BookID) REFERENCES Books(BookID),
   FOREIGN KEY (MemberID) REFERENCES Members(MemberID),
 );
 
INSERT INTO Books (Title, Author, Genre, PublishedYear, AvailableCopies) 
VALUES (1, 'The Great Gatsby', 'F. Scott Fitzgerald', 'Fiction', 1925, 5);

INSERT INTO Members (FirstName, LastName, Email, PhoneNumber, MembershipDate) 
VALUES (1, 'John', 'Doe', 'johndoe@example.com', '123-456-7890', '2024-07-10');

INSERT INTO Transactions (BookID, MemberID, BorrowDate, ReturnDate) 
VALUES (1, 1, 1, '2024-07-10', NULL);

UPDATE Books 
SET AvailableCopies = AvailableCopies - 1 
WHERE BookID = 1;

UPDATE Members 
SET Email = 'john.doe@newemail.com' 
WHERE MemberID = 1;

DELETE FROM Books 
WHERE BookID = 1;

DELETE FROM Members 
WHERE MemberID = 1;

SELECT * FROM Books;

SELECT * FROM Members;

SELECT * FROM Transactions;

SELECT Books.Title, Books.Author, Transactions.BorrowDate 
FROM Transactions 
JOIN Books ON Transactions.BookID = Books.BookID 
WHERE Transactions.MemberID = 1;


