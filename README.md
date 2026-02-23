🚔 Crime Records System Database
📌 Overview

The Crime Records System Database is designed to manage and organize information about criminals, crime cases, police officers, victims, and evidence.

Built using MySQL, this project demonstrates:

Relational database design

Foreign key relationships

Many-to-Many mappings

Role-Based Access Control (RBAC)

🗄️ Database Information

Database Name: crime_records_system

📑 Tables Structure
🔹 Criminal
Column	Description
Criminal_ID	Primary Key
Name	Criminal Name
DOB	Date of Birth
Crime_Type	Type of Crime
Arrest_Date	Date of Arrest
🔹 Crime_Case
Column	Description
Case_ID	Primary Key
Case_Type	Type of Case
Crime_Location	Location of Crime
Case_Status	Status of Case
Filed_Date	Date Filed
🔹 Police_Officer
Column	Description
Officer_ID	Primary Key
Name	Officer Name
Officer_Rank	Rank
Station_ID	Station Reference
Contact_Number	Phone Number
🔹 Victim
Column	Description
Victim_ID	Primary Key
Name	Victim Name
DOB	Date of Birth
Address	Residential Address
Contact_Number	Phone Number
🔹 Evidence
Column	Description
Evidence_ID	Primary Key
Case_ID	Foreign Key → Crime_Case
Evidence_Type	Type of Evidence
Collected_Date	Collection Date
Location_Found	Evidence Location
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

✨ Key Features

Structured relational database

Primary & Foreign Key constraints

Many-to-Many relationship implementation

Secure role-based access

Scalable and extendable structure

▶️ How to Run

Open MySQL Workbench

Create schema: crime_records_system

Run crime_records_system.sql

Insert sample data

Test using SELECT queries

Log in with different user roles to verify permissions

🔐 User Roles & Permissions
Role	Access
👑 Admin	Full access
🕵️ Investigator	Manage Criminal, Case, Evidence
👮 Officer	Manage Case & Evidence
📝 Clerk	Manage Victim
👁️ Auditor	Read-only access
📊 ER Diagram
<img width="1595" height="646" alt="ER Diagram" src="https://github.com/user-attachments/assets/6ef19235-33c0-421e-ae47-71f98b9f5b6e" />
👥 Group Members

Md Imran

Mohd Ashif Hussain

Mohd Fahim

Mohit

📜 License

This project is for educational purposes only.
