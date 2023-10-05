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
CREATE TABLE employ5
(
empid NUMBER,
empname VARCHAR2(10),
dept VARCHAR2(10),
salary NUMBER
);
```
## OUTPUT:

![S1-E5](https://github.com/MIRUDHULA-DHANARAJ/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94828147/0cd725de-2a02-4724-b4b1-0fc21820d3d1)

### Create salary_log table
## QUERY:
```
CREATE TABLE wages1_log1
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

![S2-E5](https://github.com/MIRUDHULA-DHANARAJ/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94828147/c74502c1-063a-4171-b286-9edd7df2dd25)

### PLSQL Trigger code:
## QUERY:
```
CREATE OR REPLACE TRIGGER logging_sal_update2
BEFORE UPDATE ON employ5
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

![S6-E5](https://github.com/MIRUDHULA-DHANARAJ/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94828147/20502605-5297-437c-bf88-df56831d4298)

### Inserting data into the employed table:
## QUERY:
```
insert into employ5 values(1,'Miru','IT',100000);
insert into employ5 values(2,'Div','SALES',40000);
insert into employ5 values(3,'Rev','HR',800000);
insert into employ5 values(4,'Den','SALES',30000);
insert into employ5 values(5,'Niva','IT',90000);
```

### Update the salary of an employed:
## QUERY:
```
UPDATE employ5
SET salary = 120000
where empid=3;
```

## Display the employee table:
## QUERY:
```
select * from employ;
```
## OUTPUT:

![S4-E5](https://github.com/MIRUDHULA-DHANARAJ/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94828147/71806e95-5586-4a4c-8b24-78fdaf35743e)

## Display the salary_log table:
## QUERY:
```
select * from wages_log;
```

## OUTPUT:

![S5-E5](https://github.com/MIRUDHULA-DHANARAJ/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94828147/496f50c8-b434-4f5e-9b7b-ecc4d6913009)

### Result:
The program has been implemented successfully.
