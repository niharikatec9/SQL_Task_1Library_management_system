# SQL_Task_1Library_management_system


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
   Member_shipdate DATE NOT NULL
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
VALUES ('The Great Gatsby', 'F. Scott Fitzgerald', 'Fiction', 1925, 5);

INSERT INTO Members (FirstName, LastName, Email, PhoneNumber, MembershipDate) 
VALUES ('John', 'Doe', 'johndoe@example.com', '123-456-7890', '2024-07-10');

INSERT INTO Transactions (BookID, MemberID, BorrowDate, ReturnDate) 
VALUES (1, 1, '2024-07-10', NULL);

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

