# Experiment 6: Implementation of SQL for TCL Commands

```
Name : Namachivayam T
Reg No : 212223060179
```

## Aim

To implement Transaction Control Language (TCL) commands such as `COMMIT`, `ROLLBACK`, `SAVEPOINT`, and `ROLLBACK TO SAVEPOINT` using SQL and verify transaction operations.

## Algorithm

1. Start.
2. Create a database named `COLLEGE`.
3. Select the `COLLEGE` database using the `USE` command.
4. Create the `STUDENT` table with Student ID, Name, Department, and Marks.
5. Insert student records into the `STUDENT` table.
6. Use `COMMIT` to permanently save the inserted records.
7. Start a new transaction using `START TRANSACTION`.
8. Create a savepoint named `sp1`.
9. Insert a new student record.
10. Create another savepoint named `sp2`.
11. Update the marks of an existing student.
12. Display the records to verify the changes.
13. Use `ROLLBACK TO SAVEPOINT sp2` to undo the changes made after `sp2`.
14. Display the records and verify the rollback.
15. Use `ROLLBACK TO SAVEPOINT sp1` to undo the changes made after `sp1`.
16. Display the records and verify the rollback.
17. Use `COMMIT` to permanently save the remaining transaction changes.
18. Display the final contents of the `STUDENT` table.
19. Stop.

## Procedure for Executing the SQL Program

* Open an SQL programming environment such as MySQL Workbench.
* Create a new SQL query.
* Type or paste the given TCL commands into the editor.
* Execute the commands to create the `COLLEGE` database and select it.
* Create the `STUDENT` table with the required fields.
* Insert the initial student records into the table.
* Execute the `COMMIT` command to permanently save the inserted records.
* Start a new transaction using `START TRANSACTION`.
* Create a savepoint using `SAVEPOINT sp1`.
* Insert a new student record and create another savepoint using `SAVEPOINT sp2`.
* Update the marks of an existing student and display the table contents.
* Execute `ROLLBACK TO SAVEPOINT sp2` and verify that the update is undone.
* Execute `ROLLBACK TO SAVEPOINT sp1` and verify that the insertion after `sp1` is undone.
* Execute `COMMIT` to save the remaining transaction.
* Display the final contents of the `STUDENT` table using `SELECT`.
* Observe and verify the effects of the TCL commands.

## Program

```sql id="5j8q2m"
CREATE DATABASE COLLEGE;

USE COLLEGE;

CREATE TABLE STUDENT (
    Student_ID INT PRIMARY KEY,
    Name VARCHAR(50),
    Department VARCHAR(30),
    Marks INT
);

INSERT INTO STUDENT VALUES
(101, 'Arun', 'CSE', 85);

INSERT INTO STUDENT VALUES
(102, 'Bala', 'ECE', 78);

COMMIT;

START TRANSACTION;

SAVEPOINT sp1;

INSERT INTO STUDENT VALUES
(103, 'Chris', 'EEE', 90);

SAVEPOINT sp2;

UPDATE STUDENT
SET Marks = 95
WHERE Student_ID = 101;

SELECT * FROM STUDENT;

ROLLBACK TO SAVEPOINT sp2;

SELECT * FROM STUDENT;

ROLLBACK TO SAVEPOINT sp1;

SELECT * FROM STUDENT;

COMMIT;

SELECT * FROM STUDENT;
```

## Output

### After Initial Commit

<img width="485" height="117" alt="image" src="https://github.com/user-attachments/assets/14eb0211-03bd-418e-adfb-e8b8ed6a01e5" />

### After Savepoint `sp1`

<img width="497" height="117" alt="image" src="https://github.com/user-attachments/assets/a69499aa-23dd-4599-bc05-c866363316fa" />

### After Savepoint `sp2`

<img width="497" height="146" alt="image" src="https://github.com/user-attachments/assets/12b1bc4a-16c4-44b7-94a3-511648656341" />

### After Updation

<img width="497" height="142" alt="image" src="https://github.com/user-attachments/assets/a1360d7e-62ea-4493-ace7-e9654b4ad3f9" />

### Rollback to `sp2`

<img width="497" height="143" alt="image" src="https://github.com/user-attachments/assets/82192bad-2317-4205-b290-f70ed90a6087" />

### Rollback to `sp1`

<img width="497" height="125" alt="image" src="https://github.com/user-attachments/assets/04176a42-c099-4e20-87a4-f46d04f147e5" />

### After Final Commit

<img width="498" height="126" alt="image" src="https://github.com/user-attachments/assets/9dbbd6db-c953-44f3-a10e-0efa964b86fc" />

## Result

Thus, the TCL commands `COMMIT`, `ROLLBACK`, `SAVEPOINT`, and `ROLLBACK TO SAVEPOINT` were successfully implemented, and the transaction operations were verified successfully.
