🚔 Crime Records System Database
📌 Overview

This project contains the database schema for a Crime Records System, designed to manage information about criminals, cases, police officers, victims, and evidence.

The system is built using MySQL and demonstrates relational database design, foreign key relationships, many-to-many mappings, and role-based access control.

🗄️ Database: crime_records_system
📑 Tables
🔹 Criminal

Criminal_ID (PK)

Name

DOB

Crime_Type

Arrest_Date

🔹 Crime_Case

Case_ID (PK)

Case_Type

Crime_Location

Case_Status

Filed_Date

🔹 Police_Officer

Officer_ID (PK)

Name

Officer_Rank

Station_ID

Contact_Number

🔹 Victim

Victim_ID (PK)

Name

DOB

Address

Contact_Number

🔹 Evidence

Evidence_ID (PK)

Case_ID (FK → Crime_Case)

Evidence_Type

Collected_Date

Location_Found

🔹 Criminal_Case (Many-to-Many)

Criminal_ID (FK → Criminal)

Case_ID (FK → Crime_Case)

🔹 Officer_Case (Many-to-Many)

Officer_ID (FK → Police_Officer)

Case_ID (FK → Crime_Case)

🔹 Victim_Case (Many-to-Many)

Victim_ID (FK → Victim)

Case_ID (FK → Crime_Case)

🔗 Relationships

One case can involve multiple criminals, officers, and victims.

One criminal can be linked to multiple cases.

One officer can be assigned to multiple cases.

One victim can be associated with multiple cases.

Evidence is linked to a specific case (One-to-Many relationship).

✨ Key Features

✔ Structured relational database design
✔ Implementation of Primary and Foreign Keys
✔ Many-to-Many relationship handling using junction tables
✔ Role-Based Access Control (RBAC)
✔ Data integrity using constraints
✔ Scalable structure for future enhancements
✔ Supports secure multi-user access

▶️ How to Use the Project

Open MySQL Workbench

Create a new schema named crime_records_system

Run the provided SQL file (crime_records_system.sql) to:

Create all tables

Define relationships

Create users and assign permissions

Insert sample data (if provided)

Use SQL queries such as:

SELECT to retrieve records

INSERT to add new data

UPDATE to modify records

DELETE to remove records

Log in with different user roles (Admin, Investigator, Officer, Clerk, Auditor) to test role-based permissions

📊 ER Diagram
<img width="1595" height="646" alt="ER Diagram" src="https://github.com/user-attachments/assets/6ef19235-33c0-421e-ae47-71f98b9f5b6e" />
🔐 User Roles & Permissions
👤 User Role	🔑 Access
Admin	Full access to all tables
Investigator	CRUD access to Criminal, Crime_Case, Evidence
Officer	CRUD access to Crime_Case, Evidence
Clerk	CRUD access to Victim
Auditor	Read-only access to all tables
👥 Group Members

Md Imran

Mohd Ashif Hussain

Mohd Fahim

Mohit

📜 License

This project is created for educational purposes. It may be used and modified for learning and academic submissions.
