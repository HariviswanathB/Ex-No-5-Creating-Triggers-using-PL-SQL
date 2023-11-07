# Ex-No-5-Creating-Triggers-using-PL-SQL
# DATE:
1/9/23
# AIM:
To create a Trigger using PL/SQL.

# Steps:
Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
Create a trigger named as log_salary-update.
Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
End the trigger.
Update the salary of an employee in employee table.
Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
Display the employee table, salary_log table.
# Program:
```
Create employee table
create table EMPLOYEE3 (empid NUMBER, empname VARCHAR(20), dept VARCHAR(10),salary NUMBER);
Create salary_log table
create table salary_log(log_id NUMBER, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
PLSQL Trigger code
 CREATE OR REPLACE TRIGGER log_salary_update
  2    BEFORE UPDATE ON employee3
  3    FOR EACH ROW
  4  DECLARE
  5    v_old_salary NUMBER;
  6    v_new_salary NUMBER;
  7  BEGIN
  8    v_old_salary := :OLD.salary;
  9    v_new_salary := :NEW.salary;
 10
 11    IF v_old_salary <> v_new_salary THEN
 12      INSERT INTO salary_log(empid, empname, old_salary, new_salary, update_date)
 13      VALUES (:OLD.empid, :OLD.empname, v_old_salary, v_new_salary, SYSDATE);
 14    END IF;
 15  END;
 16  /
```
# Output:

![Screenshot 2023-10-04 112522](https://github.com/HariviswanathB/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119103855/7fd3f9fe-a8dd-4348-a9c4-f68afa075617)
![Screenshot 2023-10-04 112646](https://github.com/HariviswanathB/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119103855/295252e5-7ee4-41d9-a6df-685e4808e30c)


# Result:
Hence trigger has been created using PL/SQL.
