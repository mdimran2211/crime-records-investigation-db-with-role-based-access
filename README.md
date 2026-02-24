
# 🚔 Crime Records System Database

> A relational database project built using MySQL to manage crime investigation records efficiently.

---

## 📌 Overview

The **Crime Records System Database** is designed to manage and organize information about:

- 👤 Criminals  
- 📂 Crime Cases  
- 👮 Police Officers  
- 🧍 Victims  
- 🧪 Evidence  

The system implements relational database concepts, foreign key constraints, many-to-many mappings, and role-based access control (RBAC).

---

## 🛠️ Tools & Technologies Used

- 🗄️ **MySQL** – Database creation and management  
- 🖥️ **MySQL Workbench** – Database design and execution  
- 📊 **Draw.io** – ER Diagram creation  
- 🌐 **GitHub** – Version control and project hosting  

---

## ⭐ Key Features

- ✅ Structured Relational Database Design  
- 🔗 Foreign Key Relationships  
- 🔁 Many-to-Many Relationship Handling (Junction Tables)  
- 🔐 Role-Based Access Control (RBAC)  
- 🛡️ Data Integrity using Constraints  
- 👥 Multi-user Access Support  
- 📈 ER Diagram Representation  
- 📦 Scalable and Extendable Structure  

---

## 🗄️ Database Information

**Database Name:** `crime_records_system`

---

## 📑 Tables Structure

### 1️⃣ Criminal
- Criminal_ID (PK)
- Name
- DOB
- Crime_Type
- Arrest_Date

### 2️⃣ Crime_Case
- Case_ID (PK)
- Case_Type
- Crime_Location
- Case_Status
- Filed_Date

### 3️⃣ Police_Officer
- Officer_ID (PK)
- Name
- Officer_Rank
- Station_ID
- Contact_Number

### 4️⃣ Victim
- Victim_ID (PK)
- Name
- DOB
- Address
- Contact_Number

### 5️⃣ Evidence
- Evidence_ID (PK)
- Case_ID (FK → Crime_Case)
- Evidence_Type
- Collected_Date
- Location_Found

---

## 🔁 Relationship (Junction) Tables

- Criminal_Case (Criminal ↔ Case)
- Officer_Case (Officer ↔ Case)
- Victim_Case (Victim ↔ Case)

---

## 🔗 Relationships Overview

- One case can involve multiple criminals, officers, and victims.
- One criminal can be linked to multiple cases.
- One officer can handle multiple cases.
- One victim can be linked to multiple cases.
- Evidence is connected to a specific case (One-to-Many).

---

## 👥 User Roles & Permissions

| User Role | Access |
|-----------|-----------------------------------------------|
| 🛡️ Admin | Full access to all tables |
| 🕵️ Investigator | CRUD: Criminal, Crime_Case, Evidence |
| 👮 Officer | CRUD: Crime_Case, Evidence |
| 🗂️ Clerk | CRUD: Victim |
| 📊 Auditor | Read-only access |

---

## ⚙️ How to Use the Project

### Step 1️⃣: Install Required Tools
- Install MySQL Server  
- Install MySQL Workbench  

## ⚙️ How to Use the Project

### Step 2️⃣: Create Database

- Open **MySQL Workbench** and run:


- CREATE DATABASE crime_records_system;
- USE crime_records_system;
### Step 3️⃣: Import SQL File

- Open the provided crime_records_system.sql

- Execute the script

- This will:

✅ Create all tables

- 🔗 Define relationships

- 🔐 Set up foreign keys

- 👥 Create user roles and permissions (if included)

### Step 4️⃣: Perform Database Operations

- You can now use standard SQL commands:

- SELECT – Retrieve records

- INSERT – Add new data

- UPDATE – Modify existing data

- DELETE – Remove records

- Example:
  
- SELECT * FROM Criminal;
  
### Step 5️⃣: Test Role-Based Access

- Login using different roles:

- 🛡️ Admin

- 🕵️ Investigator

- 👮 Officer

- 🗂️ Clerk

- 📊 Auditor

- Verify that each role has the correct permissions.

### 📈 ER Diagram
<img width="2991" height="1211" alt="ER 1" src="https://github.com/user-attachments/assets/629cdba7-5df0-4d1a-9b74-4559401f00fa" />

 ### 👨‍💻 Project Team

- 👤 Md Imran

- 👤 Mohammad Ashif Hussain

- 👤 Mohammad Fahim

- 👤 Mohit

### 📜 License

- This project is created for educational purposes only.
- It may be used and modified for learning and academic submissions.
