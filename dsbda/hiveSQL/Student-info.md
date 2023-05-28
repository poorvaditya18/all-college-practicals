### Hive SQL for STUDENT - INFO

### Step 1:

```
Create student1.txt and student2.txt as follows:
student1.txt:
1,John Smith,Computer Science
2,Jane Doe,Electrical Engineering
3,Michael Johnson,Mechanical Engineering
4,Sarah Williams,Chemistry
5,David Lee,Physics
6,Emily Brown,Mathematics
7,Robert Davis,English Literature
8,Lisa Wilson,Business Administration
9,James Anderson,Psychology
10,Amy Taylor,History

```

### Step 2:

```
student2.txt:
1,Programming,90
2,Electrical Circuits,75
3,Thermodynamics,88
4,Organic Chemistry,70
5,Quantum Mechanics,85
6,Calculus,82
7,English Literature,92
8,Management,78
9,Psychological Disorders,77
10,World History,83

```

### Step 3:

```
CREATE TABLE student1(
> STUDENT_ID INT,
> STUDENT_NAME STRING,
> STUDENT_BRANCH STRING
> )
> ROW FORMAT DELIMITED FIELDS TERMINATED BY ',';
```

### Step 4:

```
LOAD DATA LOCAL INPATH
> '/home/student/student1.txt'
> INTO TABLE student1;
```

### Step 5:

```
select * from student1;
```

### Step 6:

```
CREATE TABLE student2 (
> STUDENT_ID INT,
> SUBJECT STRING,
> MARKS INT
> )
> ROW FORMAT DELIMITED FIELDS TERMINATED BY ',';
```

### Step 7:

```
 LOAD DATA LOCAL INPATH
> '/home/student/student2.txt'
> INTO TABLE student2;
```

### Step 8:

```
select * from student2;
```

### Step 9:

```
SELECT s.STUDENT_ID, s.STUDENT_NAME, s.STUDENT_BRANCH,m.SUBJECT,
m.MARKS
> FROM student1 s
> JOIN student2 m ON s.STUDENT_ID = m.STUDENT_ID;
```

### Step 10:

```
SELECT s.STUDENT_ID, s.STUDENT_NAME, s.STUDENT_BRANCH,m.SUBJECT,
m.MARKS
> FROM student1 s
> JOIN student2 m ON s.STUDENT_ID = m.STUDENT_ID
> WHERE m.MARKS > 80;
```

### Step 11:

```
 select * from student2 where MARKS>80;
```
