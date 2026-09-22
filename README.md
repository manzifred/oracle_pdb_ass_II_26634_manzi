# Oracle Pluggable Database Management - Assignment II

**Student:** Manzi Fred  
**Student ID:** 26634  
**Course:** Database Development with PL/SQL (INSY 8311)  
**Instructor:** Eric Maniraguha  
**Date:** September 22, 2026  

---

## Oracle Environment

- Oracle Database 21c Enterprise Edition (21.3.0.0.0)
- CDB Name: ORCL
- Platform: Microsoft Windows x86 64-bit
- Tool used: Oracle SQL Developer (connected as CDB_Sysdba)
- OEM: Oracle Enterprise Manager Database Express

---

## Overview of Tasks

This assignment involved working with Oracle Multitenant Architecture by creating and managing Pluggable Databases (PDBs) inside a Container Database (CDB). Four tasks were completed in total.

---

## Task 1 - Create a New Pluggable Database

The goal here was to create a permanent PDB that will be used for all future class work, then create a user inside it.

I started by checking the existing PDBs and confirming the seed path, then ran the creation command from the CDB root while connected as SYSDBA.

After creation I opened it and verified it was in READ WRITE state. Then I switched the session into the PDB and created the user.

User created inside ma_pdb_26634:


Privileges granted: CONNECT, RESOURCE, DBA

Screenshots are in the screenshots/pdb_creation/ folder.

---

## Task 2 - Create and Delete a Temporary PDB

The goal was to create a second PDB, verify it exists, then fully delete it including its datafiles.

Temporary PDB created:


After creating and opening it, I ran a SELECT on v$pdbs to confirm it appeared as READ WRITE alongside ma_pdb_26634. Then I closed it with CLOSE IMMEDIATE and dropped it using INCLUDING DATAFILES to make sure nothing was left behind.

A final SELECT confirmed it was completely removed. Only PDB$SEED, ORCLPDB and ma_pdb_26634 remained.

Screenshots are in the screenshots/pdb_deletion/ folder.

---

## Task 3 - Oracle Enterprise Manager (OEM)

Accessed OEM Database Express through the browser at https://127.0.0.1:5500/em and logged in as sys with SYSDBA role.

The dashboard showed:
- CDB: ORCL running on Oracle 21.3.0.0.0 Enterprise Edition
- CDB with 2 PDBs active
- MA_PDB_26634 visible in the storage and containers sections
- Username sys visible at the top right
- Containers tab showing all containers including CDB$ROOT, PDB$SEED, ORCLPDB and MA_PDB_26634

Screenshots are in the screenshots/oem_dashboard/ folder.

---

## Challenges Faced

One issue I ran into during Task 3 was the browser blocking the OEM login page because of a self-signed certificate warning. Chrome showed a privacy error but I was able to proceed by clicking Advanced and continuing to the page. The login also had a browser popup appearing on top of the OEM form which I had to cancel before filling in the credentials. Once I entered sys with an empty container name it logged in fine.

For the PDB creation I had to first check the actual datafile path on my machine since the default paths vary between installations. My Oracle base was installed under C:\ORACLEAPP\ORADATA\ORCL\ instead of the usual C:\app path.

---







PDB created:

