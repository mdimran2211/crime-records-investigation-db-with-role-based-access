# 🚔 Crime Records Investigation Database  
### 🔐 With Role-Based Access Control (RBAC)

> A relational database project built using **MySQL** to efficiently manage crime investigation records.

---

## 📌 Overview

The **Crime Records System Database** is designed to manage and organize information about:

- 👤 Criminals  
- 📂 Crime Cases  
- 👮 Police Officers  
- 🧍 Victims  
- 🧪 Evidence  

This project demonstrates:

- 🗄️ Relational Database Design  
- 🔗 Foreign Key Relationships  
- 🔄 Many-to-Many Mapping  
- 🔐 Role-Based Access Control (RBAC)  
- ✅ Data Integrity using Constraints  

---

## 🏛️ Database Information

**Database Name:** `crime_records_system`

---

## 🗂️ Tables Structure

### 1️⃣ Criminal

| Column Name   | Description |
|--------------|------------|
| Criminal_ID (PK) | Primary Key |
| Name | Criminal Name |
| DOB | Date of Birth |
| Crime_Type | Type of Crime |
| Arrest_Date | Date of Arrest |

---

### 2️⃣ Crime_Case

| Column Name   | Description |
|--------------|------------|
| Case_ID (PK) | Primary Key |
| Case_Type | Type of Case |
| Crime_Location | Location of Crime |
| Case_Status | Status of Case |
| Filed_Date | Date Filed |

---

### 3️⃣ Police_Officer

| Column Name   | Description |
|--------------|------------|
| Officer_ID (PK) | Primary Key |
| Name | Officer Name |
| Officer_Rank | Rank |
| Station_ID | Station Reference |
| Contact_Number | Phone Number |

---

### 4️⃣ Victim

| Column Name   | Description |
|--------------|------------|
| Victim_ID (PK) | Primary Key |
| Name | Victim Name |
| DOB | Date of Birth |
| Address | Residential Address |
| Contact_Number | Phone Number |

---

### 5️⃣ Evidence

| Column Name   | Description |
|--------------|------------|
| Evidence_ID (PK) | Primary Key |
| Case_ID (FK) | References Crime_Case |
| Evidence_Type | Type of Evidence |
| Collected_Date | Date Collected |
| Location_Found | Evidence Location |

---

## 🔁 Relationship Tables (Junction Tables)

| Table Name | Purpose |
|------------|---------|
| Criminal_Case | Links Criminals ↔ Cases |
| Officer_Case | Links Officers ↔ Cases |
| Victim_Case | Links Victims ↔ Cases |

---

## 🔗 Relationships Overview

- One Case ➝ Multiple Criminals 👤  
- One Case ➝ Multiple Officers 👮  
- One Case ➝ Multiple Victims 🧍  
- One Criminal ➝ Multiple Cases 📂  
- Evidence ➝ Linked to One Case 🧪  

---

## 👥 User Roles & Permissions

| Role | Access Level |
|------|--------------|
| 🛡️ Admin | Full access to all tables |
| 🕵️ Investigator | CRUD: Criminal, Crime_Case, Evidence |
| 👮 Officer | CRUD: Crime_Case, Evidence |
| 🗃️ Clerk | CRUD: Victim |
| 📊 Auditor | Read-Only access |

---

## ⚙️ How to Run the Project

1. Open **MySQL Workbench**
2. Create schema:
   ```sql
   CREATE DATABASE crime_records_system;

   Run the provided SQL file:
3️⃣ Run the provided SQL file:

✅ Creates all tables

🔗 Defines relationships

🔐 Assigns user roles & permissions

4️⃣ Use standard SQL commands to manage data:

SELECT – Retrieve records

INSERT – Add new data

UPDATE – Modify existing data

DELETE – Remove records

📈 ER Diagram
<p align="center"> <img src="YOUR_ER_DIAGRAM_IMAGE_LINK_HERE" width="900"> </p>
👨‍💻 Project Team

👤 Md Imran

👤 Mohd Ashif Hussain

👤 Mohd Fahim

👤 Mohit

📜 License

This project is created for educational purposes only.
It may be used and modified for learning and academic submissions.
