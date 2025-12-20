# Integrated Insurance Services Management System  
### PL/SQL Capstone Project – MIS, Automation & Business Intelligence

##  Project Overview
The **Integrated Insurance Services Management System** is a PL/SQL-driven solution designed to automate, streamline, and centralize core insurance operations. The system replaces manual paperwork and scattered records with a unified, secure, and automated MIS architecture.

The database supports all major insurance activities including:
- Customer registration  
- Policy creation & assignment  
- Premium calculation  
- Payment management  
- Policy activation & expiration tracking  
- Claims submission, verification, and approval  
- Business intelligence for KPIs and dashboards  

This system demonstrates strong practical integration between:
- **Relational database design**
- **PL/SQL programming (procedures, triggers, functions, packages)**
- **MIS workflow automation**
- **Analytical reporting & BI**

---

##  Objectives
- Centralize all insurance information in a unified relational database.
- Automate repetitive operations using PL/SQL triggers & stored procedures.
- Improve accuracy, transparency, and processing speed.
- Provide MIS-enabled workflows for policy, payment, and claim management.
- Support analytics for business performance and decision-making.

---

## System Features
### **1. Customer Management**
- Register customers  
- Validate and store customer data  

### **2. Policy Management**
- Store policy types, coverage, and premium information  
- Assign policies to customers  

### **3. Payment Processing**
- Record payments  
- Auto-activate policies upon payment  
- Auto-generate receipts  
- Track outstanding or overdue payments  

### **4. Claims Processing**
- Customers submit claims  
- Admin reviews and approves/rejects claims  
- PL/SQL procedures update claim status and approved amounts  

### **5. Automation (PL/SQL)**
- Premium calculation  
- Expired policy auto-update  
- Claim validation  
- Payment verification  

### **6. Business Intelligence**
- KPI dashboards  
- Analytical queries  
- Reports on customers, revenue, claims, and policy performance  

---

##  Repository Structure


2. Phase II – Business Process Modeling (UML & BPMN)
This phase models the core business workflow of the Road Accident Reporting & Blackspot Detection System using BPMN and UML diagrams. These diagrams describe how accident information flows from field reporting to automated blackspot updates.

2.1 BPMN Diagram – Accident Reporting & Blackspot Detection
The BPMN diagram represents:

-Accident reporting by officers

-Data validation and storage

-Trigger-based blackspot calculation

-Risk-level notification

BPMN Diagram, BPMN Diagram

<img width="549" height="724" alt="image" src="https://github.com/user-attachments/assets/7fba7e0d-845d-4ed8-896f-b45fe09341e7" />

<img width="562" height="826" alt="image" src="https://github.com/user-attachments/assets/c84c7479-5aab-4947-a005-cb80456f67b8" />



2.2 Explanation
The system follows a structured accident reporting workflow. Traffic officers submit accident data (severity, location, injuries, deaths) into the system. After validation, the data is saved into the ACCIDENTS table. A PL/SQL trigger evaluates whether the accident location meets the threshold to be classified as a blackspot and updates the BLACKSPOTS table automatically.

The BPMN diagram shows the business flow between users and the system, while the UML activity diagram shows the internal system operations. Together, they demonstrate how the system supports MIS objectives such as faster reporting, automated risk detection, and improved road-safety decision-making.

3. Phase III – Logical Database Design (ERD + Data Dictionary + 3NF)
3.1 ER Diagram (Logical Model)
The ERD for the Road Accident Reporting & Blackspot Detection System contains five core entities with the required relationships:

Entity A	Relationship	Entity B	Cardinality	Notes
LOCATIONS	1 → Many	ACCIDENTS	One location can have many accidents	Location_ID = FK in ACCIDENTS
LOCATIONS	1 → 1	BLACKSPOTS	One location has one blackspot	Location_ID = UNIQUE FK
LOCATIONS	1 → Many	ANALYTICS	One location has many analytics entries	Location_ID = FK
USERS	1 → Many	ACCIDENTS	One user may record many accidents	User_ID optional FK
ERD Structure
LOCATIONS (PK: Location_ID) ├── GPS_Coordinates ├── Road_Name ├── District ├── Sector └── Created_At │ │ 1..∞ ▼ ACCIDENTS (PK: Accident_ID) ├── Location_ID (FK) ├── User_ID (FK) ├── Severity ├── Cause ├── Injuries ├── Deaths ├── Accident_Time └── Created_At

LOCATIONS 1 ─── 1 BLACKSPOTS (Unique FK: Location_ID)

LOCATIONS 1 ─── ∞ ANALYTICS (FK: Location_ID)

USERS 1 ─── ∞ ACCIDENTS (FK: User_ID)

3.2 Data Dictionary
LOCATIONS

Attribute	Type	Constraints
Location_ID	NUMBER(10)	PK, NOT NULL
GPS_Coordinates	VARCHAR2(50)	NOT NULL, UNIQUE
Road_Name	VARCHAR2(100)	NOT NULL
District	VARCHAR2(50)	NOT NULL
Sector	VARCHAR2(50)	NULL
Created_At	DATE	DEFAULT SYSDATE
ACCIDENTS

Attribute	Type	Constraints
Accident_ID	NUMBER(10)	PK, NOT NULL
Location_ID	NUMBER(10)	FK, NOT NULL
User_ID	NUMBER(10)	FK, NULL
Severity	NUMBER(1)	CHECK(Severity BETWEEN 1 AND 5)
Cause	VARCHAR2(200)	NULL
Injuries	NUMBER	DEFAULT 0
Deaths	NUMBER	DEFAULT 0
Accident_Time	TIMESTAMP WITH TIME ZONE	NOT NULL
Created_At	DATE	DEFAULT SYSDATE
BLACKSPOTS

Attribute	Type	Constraints
Blackspot_ID	NUMBER(10)	PK, NOT NULL
Location_ID	NUMBER(10)	FK, UNIQUE, NOT NULL
Risk_Level	VARCHAR2(10)	CHECK(Risk_Level IN ('High','Medium','Low'))
Total_Accidents	NUMBER	DEFAULT 0
Updated_At	DATE	DEFAULT SYSDATE
ANALYTICS

Attribute	Type	Constraints
Analytics_ID	NUMBER(10)	PK, NOT NULL
Location_ID	NUMBER(10)	FK, NOT NULL
Time_Period	DATE	NOT NULL
Total_Accidents	NUMBER	NOT NULL
Fatal_Accidents	NUMBER	NOT NULL
Updated_At	DATE	DEFAULT SYSDATE
USERS

Attribute	Type	Constraints
User_ID	NUMBER(10)	PK, NOT NULL
Username	VARCHAR2(50)	UNIQUE, NOT NULL
Role	VARCHAR2(20)	CHECK(Role IN ('Admin','Analyst','Officer'))
Password_Hash	VARCHAR2(200)	NOT NULL
Created_At	DATE	DEFAULT SYSDATE
3.3 Normalization Check (3NF)
Table	3NF Check Result
LOCATIONS	Passes 3NF
ACCIDENTS	Passes 3NF
BLACKSPOTS	Passes 3NF
ANALYTICS	Passes 3NF
USERS	Passes 3NF
 Conclusion: Entire database is fully normalized to Third Normal Form (3NF).

3.4 Assumptions
Time_Period in ANALYTICS represents an aggregation period (e.g., monthly).

Passwords stored in USERS will be encrypted/hashed.

A single Location_ID uniquely identifies a road segment blackspot.

Users can optionally be linked to accidents (for audit purposes).

BLACKSPOTS table is maintained automatically by PL/SQL triggers.

GPS coordinates are stored as unique identifiers for locations.

3.5 EER DIAGRAM
<img width="770" height="546" alt="image" src="https://github.com/user-attachments/assets/c8628f76-79e8-44a8-93a3-7c097ecab067" />


The EER Diagram for the Road Accident Reporting & Blackspot Detection System visually confirms the normalized data model (Phase III) required to support the project's automation goals. The model centers on LOCATIONS as the primary entity, which links to three critical tables: ACCIDENTS via a 1 to Many relationship to record transactional data; BLACKSPOTS via a 1 to 1 relationship to hold the single, current risk classification status (High, Medium, Low); and ANALYTICS via a 1 to Many relationship to store pre-aggregated key performance indicators (KPIs) over various time periods. This structure is essential because it allows the PL/SQL Compound Trigger (Phase VII) to check the history of 
ACCIDENTS
 for a specific 
Location ID
 and quickly update the 
BLACKSPOTS
 status, providing the near real-time intelligence needed for traffic authority decision-making.

4.Database Creation(phase IV)
Objective: Create and configure Oracle pluggable database.

4.1 Database Creation (PDB Setup)
The environment uses a dedicated Pluggable Database named tue_28248_olivier_intergrated_insurance service_db.

Command (Executed as SYSDBA):
-- Phase IV: Database Creation for PDTAS
-- Student: NIYIBIZI Olivier (ID: 28248)
-- Group: Tuesday (B)
-- Date: December 2024

-- Step 1: Create Pluggable Database
CREATE PLUGGABLE DATABASE tue_28248_olivier_PDTAS_DB
  ADMIN USER olivier_admin IDENTIFIED BY niyibizi
  ROLES = (DBA)
  FILE_NAME_CONVERT = (
    'C:\dbms_oracle\oradata\XE\pdbseed\',
    'C:\dbms_oracle\oradata\XE\tue_28248_olivier_PDTAS_DB\'
  );

-- Step 2: Open PDB
ALTER PLUGGABLE DATABASE tue_28248_olivier_PDTAS_DB OPEN;
ALTER PLUGGABLE DATABASE TUE_28248_olivier_PDTAS_DB SAVE STATE;

-- Step 3: Switch to PDB
ALTER SESSION SET CONTAINER =TUE_28248_olivier__PDTAS_DB;
4.2 Tablespace Configuration and Storage
Dedicated tablespaces were created for data, indexes, and temporary files. All data files use the AUTOEXTEND ON parameter. The main user for all object creation is road_accident_app, created with appropriate privileges (CONNECT, RESOURCE).

-- Step 4: Create Tablespaces
CREATE TABLESPACE pdta_data 
DATAFILE 'C:\dbms_oracle\oradata\XE\TUE_28248_olivier_PDTAS_DB\pdta_data01.dbf'
SIZE 50M AUTOEXTEND ON NEXT 10M MAXSIZE 500M;

CREATE TABLESPACE pdta_index
DATAFILE 'C:\dbms_oracle\oradata\XE\TUE_28248_olivier_PDTAS_DB\pdta_index01.dbf'
SIZE 20M AUTOEXTEND ON NEXT 5M MAXSIZE 200M;

CREATE TEMPORARY TABLESPACE pdta_temp
TEMPFILE 'C:\dbms_oracle\oradata\XE\TUE_28248_olivier_PDTAS_DB\pdta_temp01.dbf'
SIZE 20M AUTOEXTEND ON NEXT 5M MAXSIZE 100M;

-- Step 5: Create Application User
CREATE USER patient_track IDENTIFIED BY NIYIBIZI
DEFAULT TABLESPACE pdta_data
TEMPORARY TABLESPACE pdta_temp
QUOTA UNLIMITED ON pdta_data;

GRANT CONNECT, RESOURCE, DBA TO patient_track;

-- Verification Queries
SELECT name, open_mode FROM v$pdbs;
SELECT tablespace_name, status FROM dba_tablespaces;
SELECT username, account_status FROM dba_users;
after doing all thing ( creating and config the plugable database i create i connect it to my oracle sql developer where all the remaining phase will take place

TABLE IMPLEMENTATION & DATA INSERTION (phase V)
Database Schema Creation & Data Population
Successfully executed all CREATE TABLE statements with proper constraints, primary keys, foreign keys, and business rules. The foundation of our Road Accident Reporting System is now structurally complete and ready for data management operations. table creation

<img width="1338" height="381" alt="image" src="https://github.com/user-attachments/assets/5df463d0-9db3-43b3-a198-d30c98c7fc1e" />


Automated Primary Key Sequences
Implemented Oracle sequences for all primary key columns to ensure unique identifier generation. This automated system guarantees data integrity and prevents duplicate entries while supporting scalable data growth across all entity tables

primary key sequences

<img width="838" height="429" alt="image" src="https://github.com/user-attachments/assets/b237ae5c-2710-4948-a481-59c2f2142388" />


Geographical Road Locations Data
Populated the LOCATIONS table with 15 authentic Kigali road segments complete with GPS coordinates. This geographical foundation enables precise accident mapping and blackspot detection analysis throughout the city's road network.

table location

<img width="696" height="510" alt="image" src="https://github.com/user-attachments/assets/53d70ea0-ad40-4b76-883b-baac941e0f21" />


Comprehensive Accident Records
Loaded 10 detailed accident reports demonstrating various severity levels (Minor, Serious, Fatal) and diverse causes. Each record includes casualty statistics, timestamps, and location references for comprehensive traffic safety analysis and reporting.

table accident

<img width="1186" height="340" alt="image" src="https://github.com/user-attachments/assets/22afbcef-7ac9-42f3-a035-40108acd2ea1" />


Role-Based User Management System
Configured 5 system user accounts with distinct roles (Admin, Analyst, Operator) implementing role-based access control. This security structure ensures appropriate data access levels while maintaining system integrity and audit compliance.

table user

<img width="637" height="160" alt="image" src="https://github.com/user-attachments/assets/5cd6c4a4-23fe-4f54-9725-305928f5936b" />


Database Interaction & Transactions(PHASE VI)
procedure
first i create This PL/SQL stored procedure is used to insert a new accident report into the accidents table. It also generates a new accident ID automatically using a sequence and returns it to the caller

