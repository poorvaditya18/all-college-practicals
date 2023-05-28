## Hive SQL -> Employee-Info

### Step 0:

```
Create a employee.txt file for first table as:
101,John Smith,Manager,Human Resources
102,Jane Doe,Engineer,Engineering
103,Michael Johnson,Analyst,Finance
104,Sarah Williams,Coordinator,Marketing
105,David Lee,Developer,IT
106,Emily Brown,Assistant,Administration
107,Robert Davis,Supervisor,Operations
108,Lisa Wilson,Designer,Creative
109,James Anderson,Technician,Technical Support
110,Amy Taylor,Accountant,Finance

```

### Step 1:

```

Create another employee2.txt file for second table as:
101,50000,3
102,65000,5
103,48000,2
104,72000,1
105,55000,4
106,48000,0
107,62000,2
108,53000,3
109,48000,1
110,58000,4

```

### Step 2: Create table employee

```
CREATE TABLE emp(
> EMPLOYEE_ID INT,
> EMPLOYEE_NAME STRING,
> EMPLOYEE_DESIGNATION STRING,
> DEPARTMENT STRING
> )
> ROW FORMAT DELIMITED FIELDS TERMINATED BY ','
> ;

```

### Step 2:

```
LOAD DATA LOCAL INPATH
> '/home/student/employee.txt'
> INTO TABLE emp;
```

### Step 3:

```
 select * from emp;
```

### Step 4:

```
CREATE TABLE emp2 (
> EMPLOYEE_ID INT,
> SALARY STRING,
> LEAVES_TAKEN INT
> )
> ROW FORMAT DELIMITED FIELDS TERMINATED BY ',';

```

### Step 5:

```
LOAD DATA LOCAL INPATH
> '/home/akansha/employee2.txt'
> INTO TABLE emp2;
```

### Step 6:

```
select * from emp2;
```

### Step 7: Perform JOIN

```
SELECT e.EMPLOYEE_ID, e.EMPLOYEE_NAME, e.EMPLOYEE_DESIGNATION,
e.DEPARTMENT, s.SALARY, s.LEAVES_TAKEN
> FROM emp e
> JOIN emp2 s ON e.EMPLOYEE_ID = s.EMPLOYEE_ID;
```

### Step 8:

```
show tables;
```
