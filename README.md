# SQL_Task_1Library_management_system
# SQL_Task_students and database management
TASK ONE: LIBRARY MANAGEMENT SYSTEM

Create a database for managing a library's book inventory, members, and
borrow/return transactions. This project helps you learn basic SQL commands
and database design. Design tables for books, members, and transactions.
Write SQL queries to insert, update, delete, and retrieve data.

TASK TWO: STUDENT DATABASE MANAGEMENT

Create a database to manage student records, including
personal details, courses, and grades. This project helps you
practice creating and managing relational databases. Design
tables for students, courses, and enrollments. Write SQL
queries to manage student records. Implement joins to
combine data from multiple tableS.

STUDENT DATABASE MANAGEMENT


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


CREATE TABLE Students (
    StudentID INT PRIMARY KEY AUTO_INCREMENT,
    FirstName VARCHAR(100) NOT NULL,
    LastName VARCHAR(100) NOT NULL,
    DateOfBirth DATE NOT NULL,
    Email VARCHAR(255) UNIQUE NOT NULL,
    PhoneNumber VARCHAR(20),
    EnrollmentDate DATE NOT NULL
);

CREATE TABLE Courses (
    CourseID INT PRIMARY KEY AUTO_INCREMENT,
    CourseName VARCHAR(255) NOT NULL,
    Credits INT NOT NULL
);

CREATE TABLE Enrollments (
    EnrollmentID INT PRIMARY KEY AUTO_INCREMENT,
    StudentID INT,
    CourseID INT,
    Grade CHAR(2),
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);

INSERT INTO Students (FirstName, LastName, DateOfBirth, Email, PhoneNumber, EnrollmentDate) 
VALUES ('Jane', 'Smith', '2000-04-15', 'janesmith@example.com', '987-654-3210', '2024-07-10');

INSERT INTO Courses (CourseName, Credits) 
VALUES ('Database Systems', 3);

INSERT INTO Enrollments (StudentID, CourseID, Grade) 
VALUES (1, 1, 'A');

UPDATE Students 
SET Email = 'jane.smith@newemail.com' 
WHERE StudentID = 1;

UPDATE Courses 
SET Credits = 4 
WHERE CourseID = 1;

DELETE FROM Students 
WHERE StudentID = 1;

DELETE FROM Courses 
WHERE CourseID = 1;

SELECT * FROM Students;


