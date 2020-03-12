# sqlite3 helper

# sources
 - https://www.guru99.com/sqlite-query-insert-update.html
 - https://www.guru99.com/sqlite-view-index-trigger.html
 - https://www.sqlite.org/docs.html

# table manipulation
 - create
   ```
   create table toto(id INTEGER PRIMARY KEY autoincrement, 
                     sampleValue interger, 
                     timestamp datetime DEFAULT current_timestamp);
   ```

 - remove table
   ```
   drop table toto;
   ```

 - read content of table
   ```
   SELECT * FROM Students;
   ```
   
 - display schema
   ```   
   sqlite> .fullschema
   CREATE TABLE toto(id INTEGER PRIMARY KEY autoincrement, sampleID interger, timestamp datetime DEFAULT current_timestamp);
   /* No STAT tables available */
   ```

 -  change table scheme
 ```   
ALTER TABLE table ADD COLUMN column_definition;
   ```   
   
# change table content
 - insert
 ```   
 INSERT INTO Students(StudentId, StudentName, DepartmentId, DateOfBirth)
              VALUES(11, 'Ahmad', 4, '1997-10-12');   
              
 INSERT INTO Students VALUES(12, 'Aly', 4, '1996-10-12');
 ```   

 -  delete
 ```   
 DELETE FROM Students WHERE StudentId = 11 OR StudentId = 12;
 ```   

 -  update
 ```   
 UPDATE Students
 SET DepartmentId = 3
 WHERE StudentId = 6;
```   

# sql concept
 - primray key
 - foreign ley: https://www.sqlite.org/foreignkeys.html
 - prama (meta data)
 ```   
 PRAGMA user_version;
 ```   


# tips

## timestamp VS datetime
https://www.sqlite.org/lang_datefunc.html
```   
"timestamp" DATETIME DEFAULT CURRENT_TIMESTAMP
"timestamp" DATE DEFAULT (datetime('now','localtime')),
```   

## auto update timestamps
### with trigger
```   
CREATE TRIGGER your_table_trig AFTER UPDATE ON your_table
 BEGIN
  update your_table SET updated_on = datetime('now') WHERE user_id = NEW.user_id;
 END;

CREATE TABLE referrals(
    id INTEGER PRIMARY KEY,
    source TEXT NOT NULL,
    created_at TEXT DEFAULT CURRENT_TIMESTAMP
);
```   
### when create the table
```   
CREATE TABLE whatever(
     ....
     timestamp DATE DEFAULT (datetime('now','localtime')),
     ...
);
```   
## auto increment
Work only for primary key in sqlite3
```   
CREATE TABLE table_name(
   column1 INTEGER PRIMARY KEY AUTOINCREMENT,
   column2 datatype,
   column3 datatype,
   .....
   columnN datatype,
);
```   
