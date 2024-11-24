Purpose:
The purpose of this system is to specify requirements for a College
Auditorium Booking System designed to manage bookings for three
auditoriums. It aims to facilitate clubs in booking auditoriums for
events and sessions without conflicts in scheduling.

Target Audience:
The system is designed for college club heads, student bodies like
panel , T&P cell and in-charges who need to manage and schedule
auditorium bookings efficiently. The inclusion of role-based access
and in-charge information aims to improve the booking and
management.

Software Tools:
Software Interfaces:
IDE: Eclipse Version 2023-12 (4.30.0) for Java development.
Database: MySQL Version 8.0.32 for database management.

Database Requirements:
The database for the Auditorium Booking System includes the
following tables to manage club details, booking details, and various
roles involved in the booking process:
1. Club_Details: Stores information about each club. -
2. Club_Connections: Manages connections between clubs, club
heads, and instructors.
3. Head: Stores details about club heads,
4. Club_Head: Manages the relationship between clubs and their
heads.
5. Audi: Stores information about the auditorium.
6. Incharge: Contains information about the incharge personnel.
7. Audi_Incharge: Defines the relationship between the auditorium
and its incharge.
8. Instructor: Stores details about instructors.
9. Booking: Manages booking information for auditorium events.
10.Instructor_Booking: Manages the relationship between
instructors and bookings.
11. Login: Handles user login information for system access.

Normalization:
All tables are already in 3NF.
Create table commands of the Normalized
tables;

CREATE TABLE Club_Details (
club_email_id VARCHAR(100) PRIMARY KEY,
club_name VARCHAR(50)
);
CREATE TABLE Club_Connections (
club_email_id VARCHAR(100) PRIMARY KEY,
head_email_id VARCHAR(100),
instructor_id VARCHAR(100),
FOREIGN KEY (head_email_id) REFERENCES Head(head_email_id),
FOREIGN KEY (instructor_id) REFERENCES Instructor(i_email_id)
);

CREATE TABLE Head (
login_id email-id role
int varchar(100) varchar(100)
UNIQUE

head_email_id VARCHAR(100) PRIMARY KEY,
head_name VARCHAR(100),
head_ph VARCHAR(15)
);
CREATE TABLE Club_Head (
club_email_id VARCHAR(100),
head_id VARCHAR(100),
PRIMARY KEY (club_email_id, head_id),
FOREIGN KEY (club_email_id) REFERENCES Club_details(club_email_id),
FOREIGN KEY (head_id) REFERENCES Head(head_email_id)
);

CREATE TABLE Audi (
a_name VARCHAR(100) PRIMARY KEY,
a_capacity INT
);

CREATE TABLE Incharge (
incharge_id INT UNIQUE,
incharge_email_id VARCHAR(100) PRIMARY KEY,
incharge_name VARCHAR(50),
incharge_ph VARCHAR(15)
);
CREATE TABLE Audi_Incharge (
a_name VARCHAR(100),
incharge_email_id VARCHAR(100),
PRIMARY KEY (a_name, incharge_email_id),
FOREIGN KEY (a_name) REFERENCES Audi(a_name),
FOREIGN KEY (incharge_email_id) REFERENCES Incharge(incharge_email_id)
);
CREATE TABLE Instructor (
i_email_id VARCHAR(50) PRIMARY KEY,
i_name VARCHAR(100),
i_ph_no VARCHAR(15)
);

CREATE TABLE Instructor_Booking (
i_email_id VARCHAR(50),
booking_id INT,
PRIMARY KEY (i_email_id, booking_id),
FOREIGN KEY (i_email_id) REFERENCES Instructor(i_email_id),
FOREIGN KEY (booking_id) REFERENCES Booking(booking_id)
);

CREATE TABLE Audi_Incharge (
-> a_name VARCHAR(100),
-> incharge_email_id VARCHAR(100),
-> PRIMARY KEY (a_name, incharge_email_id),
-> FOREIGN KEY (a_name) REFERENCES Audi(a_name),
-> FOREIGN KEY (incharge_email_id) REFERENCES Incharge(incharge_email_id)
-> );
Query OK, 0 rows affected (0.05 sec

CREATE TABLE booking (
b_id INT PRIMARY KEY AUTO_INCREMENT,
audi_name VARCHAR(100),
email_id VARCHAR(100),
date DATE,
start_time TIME,
end_time TIME,
purpose VARCHAR(100),
status VARCHAR(100),
FOREIGN KEY (audi_name) REFERENCES audi(a_name)
);

CREATE TABLE login (
login_id INT UNIQUE,
email_id VARCHAR(100),
role VARCHAR(100),
PRIMARY KEY (login_id, email_id)
);
