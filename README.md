# sql-assignment-2

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
FILE_NAME_CONVERT = ('/u01/app/oracle/oradata/CDB_NAME/pdbseed/', '/u01/app/oracle/oradata/CDB_NAME/PDB_NAME/');

-- Open the newly created PDB
ALTER PLUGGABLE DATABASE PDB_NAME OPEN;

-- Save the state of the PDB
ALTER PLUGGABLE DATABASE PDB_NAME SAVE STATE;
ory 
