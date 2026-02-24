```sql
CREATE DATABASE crime_records_system;
USE crime_records_system;

-- Table: Criminal
CREATE TABLE Criminal (
    Criminal_ID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100) NOT NULL,
    DOB DATE,
    Crime_Type VARCHAR(50),
    Arrest_Date DATE
);

INSERT INTO Criminal (Name, DOB, Crime_Type, Arrest_Date) VALUES
('Rohit Sharma', '1995-06-12', 'Theft', '2025-01-10'),
('Aman Verma', '1990-09-22', 'Fraud', '2025-02-05');


-- Table: Crime_Case
CREATE TABLE Crime_Case (
    Case_ID INT PRIMARY KEY AUTO_INCREMENT,
    Case_Type VARCHAR(50),
    Crime_Location VARCHAR(100),
    Case_Status VARCHAR(50),
    Filed_Date DATE
);

INSERT INTO Crime_Case (Case_Type, Crime_Location, Case_Status, Filed_Date) VALUES
('Robbery', 'Delhi Market', 'Under Investigation', '2025-01-09'),
('Cyber Crime', 'Online Scam', 'Open', '2025-02-04');

-- Table: Police_Officer
CREATE TABLE Police_Officer (
    Officer_ID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100) NOT NULL,
    Officer_Rank VARCHAR(50) NOT NULL,
    Station_ID INT,
    Contact_Number VARCHAR(15)
);

INSERT INTO Police_Officer (Name, Officer_Rank, Station_ID, Contact_Number) VALUES
('Inspector Raj', 'Inspector', NULL, '9876543210'),
('Sub Inspector Meena', 'SI', NULL, '9123456780');

-- Table: Victim
CREATE TABLE Victim (
    Victim_ID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100) NOT NULL,
    DOB DATE,
    Address VARCHAR(200),
    Contact_Number VARCHAR(15)
);
INSERT INTO Victim (Name, DOB, Address, Contact_Number) VALUES
('Ankit Gupta', '2000-03-15', 'Lajpat Nagar, Delhi', '9988776655'),
('Pooja Singh', '1998-11-30', 'Noida Sector 15', '8877665544');

-- Table: Evidence
CREATE TABL Evidence (
    Evidence_ID INT PRIMARY KEY AUTO_INCREMENT,
    Case_ID INT,
    Evidence_Type VARCHAR(50),
    Collected_Date DATE,
    Location_Found VARCHAR(100),
    FOREIGN KEY (Case_ID) REFERENCES Crime_Case(Case_ID)
);

INSERT INTO Evidence (Case_ID, Evidence_Type, Collected_Date, Location_Found) VALUES
(1, 'CCTV Footage', '2025-01-10', 'Delhi Market'),
(2, 'Bank Transaction Record', '2025-02-06', 'Online Portal');

-- Table: Criminal_Case (Many-to-Many)
CREATE TABLE Criminal_Case (
    Criminal_ID INT,
    Case_ID INT,
    PRIMARY KEY (Criminal_ID, Case_ID),
    FOREIGN KEY (Criminal_ID) REFERENCES Criminal(Criminal_ID),
    FOREIGN KEY (Case_ID) REFERENCES Crime_Case(Case_ID)
);
INSERT INTO Criminal_Case VALUES
(1, 1),
(2, 2);

-- Table: Officer_Case (Many-to-Many)
CREATE TABLE Officer_Case (
    Officer_ID INT,
    Case_ID INT,
    PRIMARY KEY (Officer_ID, Case_ID),
    FOREIGN KEY (Officer_ID) REFERENCES Police_Officer(Officer_ID),
    FOREIGN KEY (Case_ID) REFERENCES Crime_Case(Case_ID)
);

INSERT INTO Officer_Case VALUES
(1, 1),
(2, 2);

-- Table: Victim_Case (Many-to-Many)
CREATE TABLE Victim_Case (
    Victim_ID INT,
    Case_ID INT,
    PRIMARY KEY (Victim_ID, Case_ID),
    FOREIGN KEY (Victim_ID) REFERENCES Victim(Victim_ID),
    FOREIGN KEY (Case_ID) REFERENCES Crime_Case(Case_ID)
);

INSERT INTO Victim_Case VALUES
(1, 1),
(2, 2);


-- Users and Roles

CREATE USER 'admin'@'localhost' IDENTIFIED BY 'admin123';
GRANT ALL PRIVILEGES ON crime_records_system.* TO 'admin'@'localhost';

CREATE USER 'investigator'@'localhost' IDENTIFIED BY 'invest123';
GRANT SELECT, INSERT, UPDATE, DELETE ON crime_records_system.Criminal TO 'investigator'@'localhost';
GRANT SELECT, INSERT, UPDATE, DELETE ON crime_records_system.Crime_Case TO 'investigator'@'localhost';
GRANT SELECT, INSERT, UPDATE, DELETE ON crime_records_system.Evidence TO 'investigator'@'localhost';

CREATE USER 'officer'@'localhost' IDENTIFIED BY 'officer123';
GRANT SELECT, INSERT, UPDATE, DELETE ON crime_records_system.Crime_Case TO 'officer'@'localhost';
GRANT SELECT, INSERT, UPDATE, DELETE ON crime_records_system.Evidence TO 'officer'@'localhost';

CREATE USER 'clerk'@'localhost' IDENTIFIED BY 'clerk123';
GRANT SELECT, INSERT, UPDATE, DELETE ON crime_records_system.Victim TO 'clerk'@'localhost';

CREATE USER 'auditor'@'localhost' IDENTIFIED BY 'auditor123';
GRANT SELECT ON crime_records_system.* TO 'auditor'@'localhost';

FLUSH PRIVILEGES;
```


