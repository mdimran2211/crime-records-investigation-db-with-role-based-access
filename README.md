

🚔 Crime Records System Database
<p align="center"> A relational database project built using MySQL to manage crime records efficiently. </p>
📌 Overview

The Crime Records System Database is designed to manage and organize information about:

Criminals

Crime Cases

Police Officers

Victims

Evidence

This project demonstrates:

Relational Database Design

Foreign Key Relationships

Many-to-Many Mapping

Role-Based Access Control (RBAC)

🗄️ Database Details

Database Name: crime_records_system

🧱 Database Structure
🔹 Criminal
Field	Type	Key
Criminal_ID	INT	PK
Name	VARCHAR	—
DOB	DATE	—
Crime_Type	VARCHAR	—
Arrest_Date	DATE	—
🔹 Crime_Case
Field	Type	Key
Case_ID	INT	PK
Case_Type	VARCHAR	—
Crime_Location	VARCHAR	—
Case_Status	VARCHAR	—
Filed_Date	DATE	—
🔹 Police_Officer
Field	Type	Key
Officer_ID	INT	PK
Name	VARCHAR	—
Officer_Rank	VARCHAR	—
Station_ID	INT	—
Contact_Number	VARCHAR	—
🔹 Victim
Field	Type	Key
Victim_ID	INT	PK
Name	VARCHAR	—
DOB	DATE	—
Address	VARCHAR	—
Contact_Number	VARCHAR	—
🔹 Evidence
Field	Type	Key
Evidence_ID	INT	PK
Case_ID	INT	FK → Crime_Case
Evidence_Type	VARCHAR	—
Collected_Date	DATE	—
Location_Found	VARCHAR	—
🔹 Relationship Tables
Table	Purpose
Criminal_Case	Links Criminals ↔ Cases
Officer_Case	Links Officers ↔ Cases
Victim_Case	Links Victims ↔ Cases
🔗 Relationships

One Case ➝ Multiple Criminals

One Case ➝ Multiple Officers

One Case ➝ Multiple Victims

One Criminal ➝ Multiple Cases

Evidence ➝ Linked to one Case (One-to-Many)

🔐 User Roles & Permissions
Role	Access Level
👑 Admin	Full Access
🕵️ Investigator	Manage Criminal, Case, Evidence
👮 Officer	Manage Case & Evidence
📝 Clerk	Manage Victim
👁️ Auditor	Read-Only Access
▶️ How to Run

Open MySQL Workbench

Create schema: crime_records_system

Run the SQL file

Insert sample data

Test using SELECT queries

Log in with different roles to verify permissions

📊 ER Diagram
<p align="center"> <img src="https://github.com/user-attachments/assets/6ef19235-33c0-421e-ae47-71f98b9f5b6e" width="90%"> </p>
👥 Group Members

Md Imran

Mohd Ashif Hussain

Mohd Fahim

Mohit

📜 License

This project is for educational purposes only.
