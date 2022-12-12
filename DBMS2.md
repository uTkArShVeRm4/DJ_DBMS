# What is a Database?

A database is an organised collection of related data from which you can easily retrieve and use data.

## Why is it used?
- Manages large amounts of data
- Has lots of constraints to maintain accuracy and data integrity
- Easy to update and manage data
- Data is secure

# Difference between File System and DBMS: 
|Basis| File System|	DBMS|
|----------|:-------------:|------:|
Structure	|The file system is software that manages and organizes the files in a storage medium within a computer.	|DBMS is software for managing the database.|
Data Redundancy|	Redundant data can be present in a file system.	|In DBMS there is no redundant data.
Backup and Recovery|	It doesn’t provide backup and recovery of data if it is lost.|	It provides backup and recovery of data even if it is lost.|
Query processing|	There is no efficient query processing in the file system.|	Efficient query processing is there in DBMS.|
Consistency|	There is less data consistency in the file system.|	There is more data consistency because of the process of normalization.|
Complexity|	It is less complex as compared to DBMS.|	It has more complexity in handling as compared to the file system.|
Security Constraints|	File systems provide less security in comparison to DBMS.|	DBMS has more security mechanisms as compared to file systems.|
Cost|	It is less expensive than DBMS.|	It has a comparatively higher cost than a file system.|
Data Independence|	There is no data independence.|	In DBMS data independence exists.|
User Access|	Only one user can access data at a time.|	Multiple users can access data at a time.|
Sharing| 	Data is distributed in many files. So, not easy to share data.|	Due to centralized nature sharing is easy|
Data Abstraction|	It give details of storage and representation of data|	It hides the internal details of Database|
Integrity Constraints|	Integrity Constraints are difficult to implement|	Integrity constraints are easy to implement|

# Who is DBA and what are his functions?
- Manages data integrity and security – 

    Data integrity needs to be checked and managed accurately as it protects and restricts data from unauthorized use. DBA eyes on relationships within data to maintain data integrity.
- Database Accessibility –  

    Database Administrator is solely responsible for giving permission to access data available in the database. It also makes sure who has the right to change the content.
- Database design – 

    DBA is held responsible and accountable for logical, physical design, external model design, and integrity and security control.
- Database implementation – 

    DBA implements DBMS and checks database loading at the time of its implementation.
- Query processing performance – 

    DBA enhances query processing by improving speed, performance, and accuracy.-

# Entity
An entity is a piece of data that is stored in the database. An entity can be a person, place, thing, or even an event. 

Types of entity:
1. Strong entity: Exists independently. Has primary key.
2. Weak entity: Depends on another strong entity for its existence. Has a partial key.

# Attributes
An attribute is a property or characteristic of an entity. An entity may contain any number of attributes.

Types:
- Simple
- Composite
- MultiValued
- SingleValued
- Key
- Derived
- Stored

# Keys
It is used to uniquely identify any record or row of data from the table. It is also used to establish and identify relationships between tables.

Types:
1. Primary key

    It is the first key used to identify one and only one instance of an entity uniquely. The key which is most suitable from those lists becomes a primary key.

2. Candidate key

    A candidate key is an attribute or set of attributes that can uniquely identify a tuple.
    Except for the primary key, the remaining attributes are considered a candidate key. The candidate keys are as strong as the primary key.

3. Super Key

    Super key is an attribute set that can uniquely identify a tuple. A super key is a superset of a candidate key. 

4. Foreign key

    Foreign keys are the column of the table used to point to the primary key of another table.

5. Alternate keys
    All candidate keys which are not the primary key.

# ER model

ER model stands for an Entity-Relationship model. It is a high-level data model. This model is used to define the data elements and relationship for a specified system. 

# EER model
Enhanced entity-relationship diagrams are advanced database diagrams very similar to regular ER diagrams which represent requirements and complexities of complex databases. 
It is a diagrammatic technique for displaying the Sub Class and Super Class; Specialization and Generalization; Union or Category; Aggregation etc.

# Generalization
It is a bottom – up approach in which multiple lower
level entities are combined to form a single higher level entity. It is usually used to find common 
attributes among entities to form generalized entity. 

# Specialization 
It is a top – down approach in which a higher level
entity is divided into multiple lower – level entities.
In addition to sharing the attributes of the higher 
level entity, these lower – level entities have specific
attributes of their own. It is usually used to find
subsets of an entity that has a few different, or additional attributes.

# Joins
In SQL, JOIN clause is used to combine the records from two or more tables in a database. 

## Types of SQL JOIN

- INNER JOIN

    In SQL, INNER JOIN selects records that have matching values in both tables as long as the condition is satisfied. It returns the combination of all rows from both the tables where the condition satisfies.

    Syntax;

    `SELECT table1.column1, table1.column2, table2.column1,....  FROM table1   
    INNER JOIN table2  
    ON table1.matching_column = table2.matching_column; ` 

- LEFT JOIN

    The SQL left join returns all the values from left table and the matching values from the right table. If there is no matching join value, it will return NULL.

    Syntax

    `SELECT table1.column1, table1.column2, table2.column1,....  
    FROM table1   
    LEFT JOIN table2  
    ON table1.matching_column = table2.matching_column; ` 
- RIGHT JOIN

    In SQL, RIGHT JOIN returns all the values from the values from the rows of right table and the matched values from the left table. If there is no matching in both tables, it will return NULL.

    Syntax

    `SELECT table1.column1, table1.column2, table2.column1,....  
    FROM table1   
    RIGHT JOIN table2  
    ON table1.matching_column = table2.matching_column;  `

# Cartesian join
The CARTESIAN JOIN is also known as CROSS JOIN. In a CARTESIAN JOIN there is a join for each row of one table to every row of another table. This usually happens when the matching column or WHERE condition is not specified.

- In the absence of a WHERE condition the CARTESIAN JOIN will behave like a CARTESIAN PRODUCT . i.e., the number of rows in the result-set is the product of the number of rows of the two tables.
- In the presence of WHERE condition this JOIN will function like a INNER JOIN.  

# Views
Views are created in order to store your queries as virtual
table. If there are a lot of columns and we don’t want to
use all columns and make the table simpler, we can create a
view and reuse it repeatedly. Actually, view does not store
any data however, it contains the retrieve statements to
provide reusability.

Syntax:

    CREATE VIEW view_name AS
    SELECT column1, column2.....
    FROM table_name
    WHERE condition;`

# Triggers
A trigger is a stored procedure in database which automatically invokes whenever a special event in the database occurs. For example, a trigger can be invoked when a row is inserted into a specified table or when certain table columns are being updated.  

Syntax:

    create trigger [trigger_name] 
    [before | after]  
    {insert | update | delete}  
    on [table_name]  
    [for each row]  
    [trigger_body] 

Example: 

    create trigger stud_marks 
    before INSERT 
    on 
    Student 
    for each row 
    set Student.total = Student.subj1 + Student.subj2 + Student.subj3, Student.per = Student.total * 60 / 100;    
