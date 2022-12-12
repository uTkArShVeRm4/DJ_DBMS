# Data Fragmentation
Fragmentation is a process of dividing the whole or full database into various subtables or sub relations so that data can be stored in different systems. The small pieces of sub relations or subtables are called fragments. These fragments are called logical data units and are stored at various sites. It must be made sure that the fragments are such that they can be used to reconstruct the original relation (i.e, there isn’t any loss of data).

### Advantages :

    - As the data is stored close to the usage site, the efficiency of the database system will increase
    - Local query optimization methods are sufficient for some queries as the data is available locally
    - In order to maintain the security and privacy of the database system, fragmentation is advantageous

### Disadvantages :

    - Access speeds may be very high if data from different fragments are needed
    - If we are using recursive fragmentation, then it will be very expensive

## Horizontal Fragmentation
The data / records are fragmented horizontally. i.e.; horizontal subset of table data is created and are stored in different database in DDB.
Schema of the table remains the same.

## Verical Fragmentation
Vertical fragmentation refers to the process of decomposing a table vertically by attributes are columns. In this fragmentation, some of the attributes are stored in one system and the rest are stored in other systems. 
A tuple-id is required to join back into original table.
Schema changes.

# Data Replication
Data Replication is the process of storing data in more than one site or node. It is useful in improving the availability of data. It is simply copying data from a database from one server to another server so that all the users can share the same data without any inconsistency. The result is a distributed database in which users can access data relevant to their tasks without interfering with the work of others.
There can be full replication, in which the whole database is stored at every site. There can also be partial replication, in which some frequently used fragment of the database are replicated and others are not replicated.

# Logical operators
Logical operators are used to specify conditions in the structured query language (SQL) statement. They are also used to serve as conjunctions for multiple conditions in a statement.

The different logical operators are shown below −

ALL − It is used to compare a value with every value in a list or returned by a query. Must be preceded by =, !=, >, < ,<=, or >= evaluates.

For example,

`select * from emp where salary>= ALL(1500,4000);`

AND − Returns TRUE if both component conditions are TRUE. Returns FALSE if either is FALSE; otherwise returns UNKNOWN.

For example,

`select * from emp where job=’manager’ AND deptno=20;`

OR − Return TRUE if either component condition is TRUE. Return FALSE if both are FALSE. Otherwise, return UNKNOWN.

For example,

`select * from emp where job=’manager’ OR deptno=20;`

IN − It is equivalent to any test. Equivalent to = ANY, The In operator is used to compare a value to a list of literal values that have been specified.

For example,

`select * from emp where ename IN (‘bhanu’,’ward’);`

NOT − Returns TRUE if the condition is FALSE. Returns FALSE, if it is TRUE. If it is UNKNOWN, it remains UNKNOWN.

For example,

`select * from emp where NOT (job is NULL)`
`select * from emp where NOT(salary between 2000 AND 5000);`

BETWEEN − It is used to define range limits.

For example,

If we want to find all employees whose age is in between 40 and 50 the query is as follows −

`Select * from employee E where E.age between 40 AND 50;`

LIKE − It is used to compare values to a list of literal values that are specified. “%” character is used to match any substring and “_” character is used to match any character. It expresses a pattern by using the ‘like’ comparison operator.

For example,

To display all names whose second letter is ‘b’, use the below mentioned command −

`select * from emp where ename LIKE ‘_b%’;`

To display a person details whose first letter is ‘A’ and third letter is ‘d’, use the command given below −

`Select * from emp where ename LIKE ‘A_d_’;`

# Functional Dependency
The functional dependency is a relationship that exists between two attributes. It typically exists between the primary key and non-key attribute within a table.

    X   →   Y 

The left side of FD is known as a determinant, the right side of the production is known as a dependent. 

For example:

Assume we have an employee table with attributes: Emp_Id, Emp_Name, Emp_Address.

Here Emp_Id attribute can uniquely identify the Emp_Name attribute of employee table because if we know the Emp_Id, we can tell that employee name associated with it.

Functional dependency can be written as:

     Emp_Id → Emp_Name 

We can say that Emp_Name is functionally dependent on Emp_Id.

## Types of Functional Dependencies

1. Trivial functional dependency

    A → B has trivial functional dependency if B is a subset of A.
    The following dependencies are also trivial like: A → A, B → B

    Example:

    Consider a table with two columns Employee_Id and Employee_Name.  

        {Employee_id, Employee_Name}   →    Employee_Id 

    is a trivial functional dependency as   

        Employee_Id is a subset of {Employee_Id, Employee_Name}.  

    Also, 

        Employee_Id → Employee_Id 

    and 

        Employee_Name   →    Employee_Name 

    are trivial dependencies too.

2. Non-trivial functional dependency

    A → B has a non-trivial functional dependency if B is not a subset of A.
    When A intersection B is NULL, then A → B is called as complete non-trivial.

    Example:

        ID   →    Name,  
        Name   →    DOB  

# Integrity Constraints

1. Integrity constraints are a set of rules. It is used to maintain the quality of information.
2. Integrity constraints ensure that the data insertion, updating, and other processes have to be performed in such a way that data integrity is not affected.
3. Thus, integrity constraint is used to guard against accidental damage to the database.

## Types of integrity constraints
1. Domain constraints
    - Domain constraints can be defined as the definition of a valid set of values for an attribute.
    - The data type of domain includes string, character, integer, time, date, currency, etc. The value of the attribute must be available in the corresponding domain.


2. Entity integrity constraints
    - The entity integrity constraint states that primary key value can't be null.
    - This is because the primary key value is used to identify individual rows in relation and if the primary key has a null value, then we can't identify those rows.
    - A table can contain a null value other than the primary key field.


3. Referential Integrity Constraints
    - A referential integrity constraint is specified between two tables.
    - In the Referential integrity constraints, if a foreign key in Table 1 refers to the Primary Key of Table 2, then every value of the Foreign Key in Table 1 must be null or be available in Table 2.


4. Key constraints
    - Keys are the entity set that is used to identify an entity within its entity set uniquely.
    - An entity set can have multiple keys, but out of which one key will be the primary key. A primary key can contain a unique and null value in the relational table.

# MySQL CHECK Constraint
The CHECK constraint is used to limit the value range that can be placed in a column.
If you define a CHECK constraint on a column it will allow only certain values for this column.
If you define a CHECK constraint on a table it can limit the values in certain columns based on values in other columns in the row.

The following SQL creates a CHECK constraint on the "Age" column when the "Persons" table is created. The CHECK constraint ensures that the age of a person must be 18, or older:

`CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    CHECK (Age>=18)
); `

To allow naming of a CHECK constraint, and for defining a CHECK constraint on multiple columns, use the following SQL syntax:

`CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    City varchar(255),
    CONSTRAINT CHK_Person CHECK (Age>=18 AND City='Sandnes')
); `

# On Delete Cascade
ON DELETE CASCADE clause in MySQL is used to automatically remove the matching records from the child table when we delete the rows from the parent table. It is a kind of referential action related to the foreign key.

Example:

`CREATE TABLE Payment (  
payment_id int(10) PRIMARY KEY NOT NULL,  
emp_id int(10) NOT NULL,  
amount float NOT NULL,  
payment_date date NOT NULL,  
FOREIGN KEY (emp_id) REFERENCES Employee (emp_id) ON DELETE CASCADE  
    );  `

Now when any tuple from the employee table is deleted, the corresponding tuple from the payment table is also deleted.

# Normalization

- Normalization is the process of organizing the data in the database.
- Normalization is used to minimize the redundancy from a relation or set of relations. It is also used to eliminate undesirable characteristics like Insertion, Update, and Deletion Anomalies.
- Normalization divides the larger table into smaller and links them using relationships.
- The normal form is used to reduce redundancy from the database table.

## Types of Normal Form
- 1NF:	A relation is in 1NF if it contains an atomic value.
- 2NF: 	A relation will be in 2NF if it is in 1NF and all non-key attributes are fully functional dependent on the primary key.
- 3NF: 	A relation will be in 3NF if it is in 2NF and no transition dependency exists.
- BCNF: A relation is in BCNF if it is in 3NF and X is superkey for every functional dependency (FD) X→Y in given relation. 

### Advantages

- Normalization helps to minimize data redundancy.
- Greater overall database organization.
- Data consistency within the database.
- Much more flexible database design.
- Enforces the concept of relational integrity.

### Disadvantages

- You cannot start building the database before knowing what the user needs.
- The performance degrades when normalizing the relations to higher normal forms, i.e., 4NF, 5NF.
- It is very time-consuming and difficult to normalize relations of a higher degree.
- Careless decomposition may lead to a bad database design, leading to serious problems.



# Types of Database users
1. Database Administrator(DBA):

    DBA is the person/team that designs the entire database system, provides the security, manages user accounts, access and keys.

2. Application Programmer:

    Application programmer is the person that develops the software for the end user.

3. End User:

    End user is the person actually using the software to update, retrieve and modify the data from the database.    

# Locks
Table Locking in MySQL is mainly used to solve concurrency problems. It will be used while running a transaction, i.e., first read a value from a table (database) and then write it into the table (database).

MySQL provides two types of locks onto the table, which are:

READ LOCK: This lock allows a user to only read the data from a table.

WRITE LOCK: This lock allows a user to do both reading and writing into a table.

Syntax:

    LOCK TABLES table_name [READ | WRITE]; 
    
    UNLOCK TABLES;  
# Lossless Decomposition
Lossless join decomposition is a decomposition of a relation R into relations R1, R2 such that if we perform a natural join of relation R1 and R2, it will return the original relation R. This is effective in removing redundancy from databases while preserving the original data
# States
![](https://media.geeksforgeeks.org/wp-content/uploads/20200501195048/Tt7.png)

- Active state

    The active state is the first state of every transaction. In this state, the transaction is being executed.
- Partially committed

    In the partially committed state, a transaction executes its final operation, but the data is still not saved to the database.
- Committed

    A transaction is said to be in a committed state if it executes all its operations successfully. In this state, all the effects are now permanently saved on the database system.     

- Failed state

    If any of the checks made by the database recovery system fails, then the transaction is said to be in the failed state.
- Aborted

    If any of the checks fail and the transaction has reached a failed state then the database recovery system will make sure that the database is in its previous consistent state. If not then it will abort or roll back the transaction to bring the database into a consistent state. 


# Schedules
A series of operation from one transaction to another transaction is known as schedule. It is used to preserve the order of the operation in each of the individual transaction.
# Serializabilty
Serializability of schedules ensures that a non-serial schedule is equivalent to a serial schedule. It helps in maintaining the transactions to execute simultaneously without interleaving one another. In simple words, serializability is a way to check if the execution of two or more transactions are maintaining the database consistency or not.
# TCL commands
TCL stands for Transaction control language.
A single unit of work in a database is formed after the consecutive execution of commands is known as a transaction.
There are certain commands present in SQL known as TCL commands that help the user manage the transactions that take place in a database.
- COMMIT. ROLLBACK and SAVEPOINT are the most commonly used TCL commands in SQL.
# Types of locks
- Shared Lock:
    
    Same item can have multiple shared locks.
    A.k.a Read_lock
- Exclusive Lock:

    One item can only have one exclusive lock, preventing any other transaction from locking it.
    A.k.a Write_lock
# 2 Phase Locking
Strictly two phases are followed:
- Growing phase:

    Locks are acquired but cannot be released.

- Shrinking phase:

    Locks are released but new ones cannot be acquired.
# Strict 2 pl
Untill commit happens, all exclusive locks are held.
# Difference between Union and Union-all
UNION ALL:

    COMBINES THE RESULT OF 2 QUERY AND
    DOESN'T REMOVE DUPLICATE ROWS
    AND DOESN'T SORT BY FIRST COLUMN

UNION:

    COMBINES THE RESULT OF 2 QUERY AND
    REMOVES DUPLICATE ROWS AND
    SORTS BY FIRST COLUMN
# ACID properties
- Atomicity
    The entire transaction take place at once or doesn't happen at all.

- Consistency
    Database must be consistent before and after the transaction.

- Isolation
    Multiple transactions occur independently without interference.

- Durability
    The changes of the successful transaction occurs even if the system failure occur.

# Deadlock Prevention
    In a database, a deadlock is an unwanted situation in which two or more transactions are waiting indefinitely for one another to give up locks.

- Wait-Die Scheme – 
In this scheme, If a transaction requests a resource that is locked by another transaction, then the DBMS simply checks the timestamp of both transactions and allows the older transaction to wait until the resource is available for execution.

- Wound Wait Scheme – 
In this scheme, if an older transaction requests for a resource held by a younger transaction, then an older transaction forces a younger transaction to kill the transaction and release the resource. The younger transaction is restarted with a minute delay but with the same timestamp. If the younger transaction is requesting a resource that is held by an older one, then the younger transaction is asked to wait till the older one releases it.  