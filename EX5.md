# Ex. No: 5 Creating Triggers using PL/SQL

### AIM: To create a Trigger using PL/SQL.

### Steps:
```
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.
```
### Program:
### Create employee table
## QUERY:
```
CREATE TABLE empl
(
empid NUMBER,
empname VARCHAR2(10),
dept VARCHAR2(10),
salary NUMBER
);
```
## OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94828147/3747e23a-3b4c-4c18-9101-9ac0f7873dfe)

### Create salary_log table
## QUERY:
```
CREATE TABLE wages_log
(
log_id NUMBER GENERATED ALWAYS AS IDENTITY,
empid NUMBER,
empname VARCHAR2(10),
old_salary NUMBER,
new_salary NUMBER,
update_date DATE
);
```
## OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94828147/f389398e-9fc0-4169-96e8-e2574b8db4d6)


### PLSQL Trigger code:
## QUERY:
```
CREATE OR REPLACE TRIGGER logging_sal_update
BEFORE UPDATE ON empl
FOR EACH ROW
BEGIN
IF :OLD.salary != :NEW.salary THEN
INSERT INTO wages_log (empid, empname, old_salary, new_salary, update_date)
VALUES (:OLD.empid, :OLD.empname, :OLD.salary, :NEW.salary, SYSDATE);
END IF;
END;
/
```
### Output:

![image](https://github.com/MIRUDHULA-DHANARAJ/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94828147/b71f1b4c-3f98-451f-9a7c-611c86aa6a3f)

### Inserting data into the employed table:
## QUERY:
```
insert into empl values(1,'Divya','IT',100000);
insert into empl values(2,'Sujithra','SALES',50000);
insert into empl values(3,'Pavithra','HR',110000);
insert into empl values(4,'Saranya','SALES',50000);
insert into empl values(5,'Dharshini','IT',100000);
```
### OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94828147/20a43da4-d975-496e-b33c-1f337144596d)

### Update the salary of an employed:
## QUERY:
```
UPDATE empl
SET salary = 120000
where empid=3;
```
## OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94828147/29052f2f-e82f-43d2-b297-479c1b600b54)
## Display the employee table:
## QUERY:
```
select * from empl;
```
## OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94828147/caf36fc1-1dce-44b8-8d7a-463636255fa4)

## Display the salary_log table:
## QUERY:
```
select * from wages_log;
```

## OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94828147/5e56b005-9d1b-419e-b5c3-2a1218ceab49)

### Result:
The program has been implemented successfully.
