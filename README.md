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
CREATE TABLE <table name> (
    <column name 1> <datatype> ,
    <column name 2> <datatype>
);
```
2. With primary key, Without constraint
```sql
CREATE TABLE <table name> (
    <column name 1> <datatype> ,
    <column name 2> <datatype> ,
    PRIMARY KEY ( <column name 1>)
);
```
3. With primary key and foreign key constraint
```sql
CREATE TABLE <table name> (
    <column name 1> <datatype> ,
    <column name 2> <datatype> ,
    CONSTRAINT <constraint name 1> PRIMARY KEY ( <column name 1> ),
    CONSTRAINT <constraint name 2> FOREIGN KEY ( <column name 2> )
);
```
4. Check Constraints
```sql
CREATE TABLE <table name> (
    <column name 1> <datatype> ,
    <column name 2> <datatype> ,
    CHECK ( <column name 1> in (values)),
    CHECK ( <column name 2> between <val1> and <val2> )
);
```
5. Sequence Creation
```sql
CREATE SEQUENCE <sequence name>
INCREMENT BY <increment value> 
START WITH <starting value>;
```
```sql
CREATE SEQUENCE my_sequence
START WITH 1
INCREMENT BY 1;

INSERT INTO my_table (id, name)
VALUES (nextval('my_sequence'), 'John Doe');
```
6. Role Creation
```sql
CREATE ROLE <role name>;
```

### Alter 
1. Add new columns
```sql
ALTER TABLE <table name> ADD ( <column name> <datatype> );
```
2. Modify datatype or increase/decrease column width
```sql
ALTER TABLE <table name> MODIFY ( <column name> <new datatype> );
```
3. Delete Columns or delete constraints
```sql
ALTER TABLE <table name> DROP COLUMN <columm name>;
ALTER TABLE <table name> DROP CONSTRAINT <constraint name>;
```
Note: Constraints addition and column changing (data type or increasing width) can only be done
if column values are null. 

### Truncate
1. Remove the rows, not the defintion
```sql
TRUNCATE TABLE <table name>;
```

### Drop 
1. Remove rows and the definition
```sql
DROP TABLE <table name>;
```

### Rename
```sql
RENAME <old table name> TO <new table namme>;
```

## DML 
### Insert
```sql
INSERT INTO <table name> VALUES (val1, val2, .. , '');
```
### Select 
1. Simple Select
```sql
SELECT * FROM <table name>;
SELECT <col1>, <col2> FROM <table name>;
```
2. Alias Name
```sql
SELECT <col1> as c1, <col2> as c2 FROM <table name>;
```
3. Distint Clause
```sql
SELECT DISTINCT <col1> FROM <table name>;
```
4. Where Clause
```sql
SELECT <col1>, <col2> FROM <table name> WHERE <conditions>;
```
5. Select to create table
```sql
CREATE TABLE <table name> AS SELECT <column names> FROM <table name>;
```
6. Copy only table definition
```sql
CREATE TABLE <table name> AS SELECT <column names> FROM <table name> WHERE 1=2;
```
7. Select to Insert
```sql
INSERT INTO <table> (SELECT <column names> FROM <table>);
```
### Update
1. Simple Update
```sql
UPDATE <table name> SET <col> = <new value>;
```
2. Using Where Clause
```sql
UPDATE <table name> SET <col> = <new value>, <col2> = <new value> WHERE <conditions>;
```
### Delete
1. Delete all rows
```sql
DELETE FROM <table name>;
```
2. Where Clause
```sql
DELETE FROM <table name> WHERE <conditions>;
```

## TCL
### Commit
```sql
COMMIT;
```
### Save Point
```sql
SAVEPOINT <save point>;
```
### Rollback
```sql
ROLLBACK;
ROLLBACK <save point>;
```

## DCL 
### Grant
1. Grant all privileges
```sql
GRANT ALL ON <object name> TO <username>;
```
2. Grant certain privileges
```sql
GRANT <privileges> ON <object name> TO <username>;
```
3. Grant Execute Privilege
```sql
GRANT EXECUTE ON <function name> TO <username>;
```
4. Setting Privilege to Role
```sql
GRANT <any DML command> TO <role name>;
GRANT <role name> TO <user name>;
```

### Revoke
```sql
REVOKE <privileges> ON <object name> FROM <username>;
REVOKE <any DML commmand> ON <table name> FROM <username>;
```

## Operations 
| Type |  Symbol/Keyword  |
| :----------|:--------:| :----------:| :---: | :---------: |
| Arithmetic | +, -, *, / 
| Comparison | =, !=, <, <=, >, >=, between, not between, in, not in, like, not like | 
| Logical | and, or, not | 
