
-- Database: crime_records_system


-- Create database
CREATE DATABASE IF NOT EXISTS crime_records_system;
USE crime_records_system;


-- Table: Criminal

CREATE TABLE IF NOT EXISTS Criminal (
    Criminal_ID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100) NOT NULL,
    DOB DATE,
    Crime_Type VARCHAR(50),
    Arrest_Date DATE
);


-- Table: Crime_Case

CREATE TABLE IF NOT EXISTS Crime_Case (
    Case_ID INT PRIMARY KEY AUTO_INCREMENT,
    Case_Type VARCHAR(50),
    Crime_Location VARCHAR(100),
    Case_Status VARCHAR(50),
    Filed_Date DATE
);

-- ===============================
-- Table: Police_Officer
-- ===============================
CREATE TABLE IF NOT EXISTS Police_Officer (
    Officer_ID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100) NOT NULL,
    Officer_Rank VARCHAR(50) NOT NULL,
    Station_ID INT,
    Contact_Number VARCHAR(15)
);

-- ===============================
-- Table: Victim
-- ===============================
CREATE TABLE IF NOT EXISTS Victim (
    Victim_ID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100) NOT NULL,
    DOB DATE,
    Address VARCHAR(200),
    Contact_Number VARCHAR(15)
);

-- ===============================
-- Table: Evidence
-- ===============================
CREATE TABLE IF NOT EXISTS Evidence (
    Evidence_ID INT PRIMARY KEY AUTO_INCREMENT,
    Case_ID INT,
    Evidence_Type VARCHAR(50),
    Collected_Date DATE,
    Location_Found VARCHAR(100),
    FOREIGN KEY (Case_ID) REFERENCES Crime_Case(Case_ID)
);

-- ===============================
-- Table: Criminal_Case (Many-to-Many)
-- ===============================
CREATE TABLE IF NOT EXISTS Criminal_Case (
    Criminal_ID INT,
    Case_ID INT,
    PRIMARY KEY (Criminal_ID, Case_ID),
    FOREIGN KEY (Criminal_ID) REFERENCES Criminal(Criminal_ID),
    FOREIGN KEY (Case_ID) REFERENCES Crime_Case(Case_ID)
);

-- ===============================
-- Table: Officer_Case (Many-to-Many)
-- ===============================
CREATE TABLE IF NOT EXISTS Officer_Case (
    Officer_ID INT,
    Case_ID INT,
    PRIMARY KEY (Officer_ID, Case_ID),
    FOREIGN KEY (Officer_ID) REFERENCES Police_Officer(Officer_ID),
    FOREIGN KEY (Case_ID) REFERENCES Crime_Case(Case_ID)
);

-- ===============================
-- Table: Victim_Case (Many-to-Many)
-- ===============================
CREATE TABLE IF NOT EXISTS Victim_Case (
    Victim_ID INT,
    Case_ID INT,
    PRIMARY KEY (Victim_ID, Case_ID),
    FOREIGN KEY (Victim_ID) REFERENCES Victim(Victim_ID),
    FOREIGN KEY (Case_ID) REFERENCES Crime_Case(Case_ID)
);

-- ===============================
-- Users and Roles
-- ===============================

-- Admin user: full access
CREATE USER 'admin'@'localhost' IDENTIFIED BY 'admin123';
GRANT ALL PRIVILEGES ON crime_records_system.* TO 'admin'@'localhost';

-- Investigator: access to Criminal, Crime_Case, Evidence
CREATE USER 'investigator'@'localhost' IDENTIFIED BY 'invest123';
GRANT SELECT, INSERT, UPDATE, DELETE ON crime_records_system.Criminal TO 'investigator'@'localhost';
GRANT SELECT, INSERT, UPDATE, DELETE ON crime_records_system.Crime_Case TO 'investigator'@'localhost';
GRANT SELECT, INSERT, UPDATE, DELETE ON crime_records_system.Evidence TO 'investigator'@'localhost';

-- Officer: access to Crime_Case and Evidence
CREATE USER 'officer'@'localhost' IDENTIFIED BY 'officer123';
GRANT SELECT, INSERT, UPDATE, DELETE ON crime_records_system.Crime_Case TO 'officer'@'localhost';
GRANT SELECT, INSERT, UPDATE, DELETE ON crime_records_system.Evidence TO 'officer'@'localhost';

-- Clerk: access to Victim
CREATE USER 'clerk'@'localhost' IDENTIFIED BY 'clerk123';
GRANT SELECT, INSERT, UPDATE, DELETE ON crime_records_system.Victim TO 'clerk'@'localhost';

-- Auditor: read-only access to all tables
CREATE USER 'auditor'@'localhost' IDENTIFIED BY 'auditor123';
GRANT SELECT ON crime_records_system.* TO 'auditor'@'localhost';

-- Apply privileges
FLUSH PRIVILEGES;
