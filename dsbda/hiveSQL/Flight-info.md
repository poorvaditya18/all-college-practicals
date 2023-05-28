## Hive SQL For Flight Info

### Step 1: start localhost

```
ssh localhost
```

### Step 2: stop all services of hadoop

```
stop-all.sh
```

### Step 3: start and initialise the master node

```
hadoop namenode -format
```

### Step 4: start hadoop node

```
start-all.sh
```

### Step 5: start hive

```
hive
```

### Step 6:

```
SHOW DATABASES;
```

### Step 7:

```
 CREATE DATABASE flight_info_system;
```

### Step 8:

```
SHOW TABLES;
```

### Step 9:

```
CREATE TABLE flight_info(
> FL_NUM INT,
> ORIGIN_AIRPORT_ID INT,
> ORIGIN STRING,
> DEST_AIRPORT_ID INT,
> DEST STRING,
> DEP_TIME INT,
> DEP_DELAY INT,
> ARR_TIME INT,
> ARR_DELAY INT
> )
> ROW FORMAT DELIMITED FIELDS TERMINATED BY ','
> tblproperties ("skip.header.line.count"="1");
```

### Step 10: Insert the csv data into flight table

```
> LOAD DATA LOCAL INPATH
> '/home/student/flightdata.csv'
> INTO TABLE flight_info;
```

### Step 11:

```
select count(*) from flight_info;
```

### Step 12:

```
ALTER TABLE flight_info RENAME TO flight_info_internal;
```

### Step 13:

`show tables;`

### Step 14:

`DROP TABLE flight_info_internal;`

### Step 15:

`show tables;`

### Step 16:

```
> CREATE EXTERNAL TABLE flight_info(
> FL_NUM INT,
> ORIGIN_AIRPORT_ID INT,
> ORIGIN STRING,
> DEST_AIRPORT_ID INT,
> DEST STRING,
> DEP_TIME INT,
> DEP_DELAY INT,
> ARR_TIME INT,
> ARR_DELAY INT
> )
> ROW FORMAT DELIMITED FIELDS TERMINATED BY ','
> STORED AS TEXTFILE
> LOCATION '/home/akansha/flightdata.txt'
> tblproperties ("skip.header.line.count"="1");

```

### Step 17:

`select count(*) from flight_info;`

### Step 18:

```
LOAD DATA LOCAL INPATH
> '/home/akansha/flightdata.csv'
> INTO TABLE flight_info;
```

### Step 19:

`show tables;`

### Step 20:

`select count(*) from flight_info;`

### Step 21:

` DROP TABLE flight_info;`

### Step 22: IN NEW TERMINAL, COPY flightdata.txt FILE INTO HDFS USING COMMAND :

`hdfs dfs -copyFromLocal flightdata.txt /data1/  `

### Step 23: External table because -> if we delete table from hive it should not delete from hadoop.

```CREATE EXTERNAL TABLE flight_info(
> FL_NUM INT,
> ORIGIN_AIRPORT_ID INT,
> ORIGIN STRING,
> DEST_AIRPORT_ID INT,
> DEST STRING,
> DEP_TIME INT,
> DEP_DELAY INT,
> ARR_TIME INT,
> ARR_DELAY INT
> )
> ROW FORMAT DELIMITED FIELDS TERMINATED BY ','
> STORED AS TEXTFILE
> LOCATION '/data1'
> tblproperties ("skip.header.line.count"="1");
```

### Step 24:

```
select count(*) from flight_info;
```

### Step 25:

```
INSERT INTO TABLE flight_info
VALUES(1872,10397,"ATL",14757,"SEA",1111,-2,1316,-24);
```

### Step 26:

```
ALTER TABLE flight_info
> ADD COLUMNS (cancelled BOOLEAN);
```

### Step 27:

```
describe flight_info;
```

### Step 28:

```
ALTER TABLE flight_info
> SET TBLPROPERTIES ('default.cancelled'='False');
```

### Step 29:

```
SELECT AVG(DEP_DELAY) AS average
> FROM flight_info
> WHERE DEP_TIME=2008;
```
