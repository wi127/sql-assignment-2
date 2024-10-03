# sql-assignment-2
- Name: Nkusi william
- ID: 22980

This repository contains the steps and SQL queries used for creating and deleting a Pluggable Database (PDB) in an Oracle 19c environment.

## Step-by-Step Guide

### 1. Creating a Pluggable Database (PDB)

The following SQL commands were used to create a new PDB:

```sql
-- Switch to the root container
ALTER SESSION SET CONTAINER=CDB$ROOT;

-- Create a new pluggable database
CREATE PLUGGABLE DATABASE PDB2 
ADMIN USER PDB_ADMIN IDENTIFIED BY PASSWORD 
FILE_NAME_CONVERT = ('C:\APP\NKUSI\PRODUCT\21C\ORADATA\XE\PDB$SEED\','C:\APP\NKUSI\PRODUCT\21C\ORADATA\XE\PDB_NAME\');

-- Open the newly created PDB
ALTER PLUGGABLE DATABASE PDB2 OPEN;

-- Save the state of the PDB
ALTER PLUGGABLE DATABASE PDB2 SAVE STATE;
ory
```
Explanation:
- ALTER SESSION SET CONTAINER=CDB$ROOT: This command ensures we are working in the root container of the multitenant database architecture.
- CREATE PLUGGABLE DATABASE: This command creates a new PDB. We specify the admin user, password, and file paths for data storage.
- ALTER PLUGGABLE DATABASE OPEN: Opens the newly created PDB to make it operational.
- SAVE STATE: Saves the state of the PDB, so it opens automatically when the CDB starts.

### 2. Deleting a Pluggable Database (PDB)
The following SQL commands were used to delete the PDB:

```sql
-- Switch to the root container
ALTER SESSION SET CONTAINER=CDB$ROOT;

-- Close the PDB before dropping it
ALTER PLUGGABLE DATABASE PDB2 CLOSE IMMEDIATE;

-- Unplug the PDB
ALTER PLUGGABLE DATABASE PDB2 UNPLUG INTO 'C:\APP\NKUSI\PRODUCT\21C\ORADATA\XE\PDB_NAME.xml';

-- Drop the PDB
DROP PLUGGABLE DATABASE PDB2 INCLUDING DATAFILES;
```
Explanation:
- CLOSE IMMEDIATE: Ensures the PDB is closed before dropping.
- UNPLUG INTO: Unplugs the PDB, creating an XML file with its metadata.
- DROP INCLUDING DATAFILES: Drops the PDB and deletes its associated data files from the filesystem.

### 3. screenshoot

1. Display all PDBS:
 
<img width="670" alt="Screenshot 2024-10-03 093702" src="https://github.com/user-attachments/assets/f4d27311-33d9-4dd9-a671-32dda1d4c1f5">

 2. Show path of PDBs:
    
<img width="673" alt="Screenshot 2024-10-03 101701" src="https://github.com/user-attachments/assets/6d2d8d3e-4273-489d-8a4b-7bc65acabbe4">

3. Creating PDB:   

<img width="675" alt="Screenshot 2024-10-03 105157" src="https://github.com/user-attachments/assets/e9f53a7a-e04c-4612-bfb9-77c3ae2a5eb3">

4.  Deleting Pluggable Database (PDB):
   
<img width="675" alt="Screenshot 2024-10-03 110022" src="https://github.com/user-attachments/assets/dddc05ad-3c50-4426-b592-8656aeb5becf">

   


