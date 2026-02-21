# Crime Records System Database

## Overview
This project contains the **database schema** for a Crime Records System, designed to manage information about criminals, cases, police officers, victims, and evidence. The system supports multiple user roles with different access levels.

---

## Database: `crime_records_system`

### Tables

1. **Criminal**
   - `Criminal_ID` (PK)
   - `Name`
   - `DOB`
   - `Crime_Type`
   - `Arrest_Date`

2. **Crime_Case**
   - `Case_ID` (PK)
   - `Case_Type`
   - `Crime_Location`
   - `Case_Status`
   - `Filed_Date`

3. **Police_Officer**
   - `Officer_ID` (PK)
   - `Name`
   - `Officer_Rank`
   - `Station_ID`
   - `Contact_Number`

4. **Victim**
   - `Victim_ID` (PK)
   - `Name`
   - `DOB`
   - `Address`
   - `Contact_Number`

5. **Evidence**
   - `Evidence_ID` (PK)
   - `Case_ID` (FK → Crime_Case)
   - `Evidence_Type`
   - `Collected_Date`
   - `Location_Found`

6. **Criminal_Case** (Many-to-Many)
   - `Criminal_ID` (FK → Criminal)
   - `Case_ID` (FK → Crime_Case)

7. **Officer_Case** (Many-to-Many)
   - `Officer_ID` (FK → Police_Officer)
   - `Case_ID` (FK → Crime_Case)

8. **Victim_Case** (Many-to-Many)
   - `Victim_ID` (FK → Victim)
   - `Case_ID` (FK → Crime_Case)

---

## Relationships
- One **case** can involve multiple **criminals**, **officers**, and **victims**.  
- One **criminal** can be linked to multiple **cases**.  
- Evidence is linked to a specific **case**.  
- ER diagram can be added here as a reference (optional: screenshot from MySQL Workbench).

---

## User Roles & Permissions

| User Role      | Access                                                |
|----------------|------------------------------------------------------|
| Admin          | Full access to all tables                             |
| Investigator   | CRUD access to Criminal, Crime_Case, Evidence        |
| Officer        | CRUD access to Crime_Case, Evidence                  |
| Clerk          | CRUD access to Victim                                 |
| Auditor        | Read-only access to all tables                        |

---

## Usage
1. Open **MySQL Workbench**.  
2. Run the SQL file `crime_records_system.sql` to create the database and all tables.  
3. Users can access the database using their assigned roles.  
4. You can link tables using foreign keys to maintain data integrity.

---

## ER Diagram
![ER Diagram with DB](https://github.com/user-attachments/assets/cd5c1adf-f25c-4e47-84b1-aa5b06a68618)



---

## License
This project is for educational purposes. Feel free to use and modify the database schema.
