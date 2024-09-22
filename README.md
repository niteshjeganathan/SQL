# SQL (Structured Query Language)

## Introduction
### Categories of Commands
* Data Definition Language - (Sets up, changes and removes tables)
  * Create
  * Alter
  * Drop
  * Rename
  * Truncate
* Data Manipulation Language - (Adds, changes, retrieves and removes rows in DB) 
  * Insert
  * Delete
  * Update
* Data Control Language - (Gives or removes access rights)
  * Grant
  * Revoke
* Transaction Control Language - (Manage changes made by DML)
  * Commit
  * Rollback
  * Save Point 

### Oracle Data Types
| Type Name  |  Syntax  | Description | Range | Valid Data
| :----------|:--------:| :----------:| :---: | :---------: |
| Character | char(length) | Fixed Length Character | 1 - 2000 bytes | '12345' |
| Character | varchar2(length) | Variable Length Character | 1 - 4000 bytes | '12345' | 
| Number | number | Any Integer | Integer range | 123.43 | 
| Date | date | Fixed Date Length | Date range |  '03-jan-2021' |
| Long | Long | Variable Length character (Only once in table) | Max 2GB | 'ggfgg...' |
| Raw | Raw | Binary data or byte strings | Max 2000 bytes | - |
| Long Raw | Long raw | Binary data of variable length | Max 2BG | - |
| Large Object | CLOB | Character Object with single byte Character | Max 4GB | - |
| Large Object | BLOB | Large Binary Objects, graphics, videos, sound | Max 4GB | - |
| Large Object | BFILE | File pointers | Max 4GB | - |
| Time | Timestamp | Date with time | - | '24-sep-75:12:12'|

## DDL 
### Create 
1. Simple Creation
```sql
CREATE TABLE <table name> ( <column name 1> <datatype> , <column name 2> <datatype> );
```
2. With primary key, Without constraint
```
CREATE TABLE <table name> ( <column name 1> <datatype> , <column name 2> <datatype> , PRIMARY KEY ( <column name 1> );
```
3. With primary key and foreign key constraint
```
CREATE TABLE <table name> ( <column name 1> <datatype> , <column name 2> <datatype> , CONSTRAINT <constraint name 1> PRIMARY KEY ( <column name 1> , CONSTRAINT <constraint name 2> FOREIGN KEY ( <column name 2> );
```

