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
CREATE PLUGGABLE DATABASE PDB_NAME 
ADMIN USER PDB_ADMIN IDENTIFIED BY PASSWORD 
FILE_NAME_CONVERT = ('C:\APP\NKUSI\PRODUCT\21C\ORADATA\XE\PDB$SEED\','C:\APP\NKUSI\PRODUCT\21C\ORADATA\XE\PDB_NAME\');

-- Open the newly created PDB
ALTER PLUGGABLE DATABASE PDB_NAME OPEN;

-- Save the state of the PDB
ALTER PLUGGABLE DATABASE PDB_NAME SAVE STATE;
ory
```
### 2. Deleting a Pluggable Database (PDB)
The following SQL commands were used to delete the PDB:

```sql
-- Switch to the root container
ALTER SESSION SET CONTAINER=CDB$ROOT;

-- Close the PDB before dropping it
ALTER PLUGGABLE DATABASE PDB_NAME CLOSE IMMEDIATE;

-- Unplug the PDB
ALTER PLUGGABLE DATABASE PDB_NAME UNPLUG INTO 'C:\APP\NKUSI\PRODUCT\21C\ORADATA\XE\PDB_NAME.xml';

-- Drop the PDB
DROP PLUGGABLE DATABASE PDB_NAME INCLUDING DATAFILES;
```
### 3. screenshoot
<img width="670" alt="Screenshot 2024-10-03 093702" src="https://github.com/user-attachments/assets/f4d27311-33d9-4dd9-a671-32dda1d4c1f5">

<img width="673" alt="Screenshot 2024-10-03 101701" src="https://github.com/user-attachments/assets/6d2d8d3e-4273-489d-8a4b-7bc65acabbe4">



