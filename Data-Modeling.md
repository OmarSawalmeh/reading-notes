# **Sequelize (Data Modeling) :**
---
---
### **SQL vs NoSQL**
- **SQL** databases are primarily called as Relational Databases (RDBMS); whereas <br />**NoSQL** database are primarily called as non-relational or distributed database.<br />
- **SQL** databases are table based databases whereas <br />**NoSQL** databases are document based, key-value pairs, graph databases or wide-column stores.<br />
- **SQL** databases have predefined schema whereas <br />**NoSQL** databases have dynamic schema for unstructured data.<br />
- **SQL** databases are vertically scalable whereas the <br />**NoSQL** databases are horizontally scalable.<br />

- **SQL** databases uses SQL ( structured query language ) for defining and manipulating the data, which is very powerful.<br /> In **NoSQL** database, queries are focused on collection of documents. Sometimes it is also called as UnQL (Unstructured Query Language). The syntax of using UnQL varies from database to database.<br />

- **SQL** database examples: MySql, Oracle, Sqlite, Postgres and MS-SQL.<br /> **NoSQL** database examples: MongoDB, BigTable, Redis, RavenDb, Cassandra, Hbase, Neo4j and CouchDb.<br />
---
### **SQL Database Examples :**
1. **MySQL Community Edition**
MySQL database is very popular open-source database. It is generally been stacked with apache and PHP, although it can be also stacked with nginx and server side javascripting using Node js. The following are some of MySQL benefits and strengths.

2. **MS-SQL Server Express Edition**
It is a powerful and user friendly database which has good stability, reliability and scalability with support from Microsoft. The following are some of MS-SQL benefits and strengths.

3. **Oracle Express Edition**
It is a limited edition of Oracle Enterprise Edition server with certain limitations. This database is free for development and deployment. The following are some of Oracle benefits and strengths.

### **NoSQL Database Examples :**
1. **MongoDB**<br />
**Mongodb** is one of the most popular document based NoSQL database as it stores data in JSON like documents. It is non-relational database with dynamic schema. It has been developed by the founders of DoubleClick, written in C++ and is currently being used by some big companies like The New York Times, Craigslist, MTV Networks. The following are some of MongoDB benefits and strengths:
    - Speed: For simple queries, it gives good performance, as all the related data are in single document which eliminates the join operations.
    - Scalability: It is horizontally scalable i.e. you can reduce the workload by increasing the number of servers in your resource pool instead of relying on a stand alone resource.
    - Manageable: It is easy to use for both developers and administrators. This also gives the ability to shard database
    - Dynamic Schema: Its gives you the flexibility to evolve your data schema without modifying the existing data

2. **CouchDB**<br />
**CouchDB** is also a document based NoSQL database. It stores data in form of JSON documents.

3. **Redis** <br />
**Redis** is another Open Source NoSQL database which is mainly used because of its lightening speed. It is written in ANSI C language.

---
### **Data Modeling Concepts :**
When working with SQL databases it is often useful to create diagrams of the database tables and their relationships.  These may be done during the design process, as  your data modeling, or once the database is created, in order to document the tables’ dependencies.  As I explain various concepts in my lessons, I’ll sometimes use models to illustrate my points.

There are many types of modeling software you can use to create models, such as MySql Workbench, which not only create smart looking diagrams, but also generate the code to create the database!  In my case, since I’m trying to keep the diagrams simple, and I don’t have a need to generate code, I’m going to create my own diagrams.  They are loosely based on the IDEF1X notation.

![](https://www.essentialsql.com/wp-content/uploads/2021/11/Database-Table-Data-Modeling.png)<br />
**The diagram above shows my method to model a relational database table.  The major elements that are depicted include:**

- **The Table Name**, which is located at the top of the table. 

- **The Primary Keys.**  Remember the primary keys uniquely identify each row in a table.  A table typically has one primary key, but can have more.  When the key has more than one column, it is called a compound key.

- **Table Columns** – There can be one or more table columns.  To keep the diagrams simple, I don’t show the data types.  I may introduce those later when we focus on more comprehensive modeling.

- **Foreign Key** – This is a column or set of columns which match a primary key in another table.

**Data Modeling – Table Relationships**<br />
![](https://www.essentialsql.com/wp-content/uploads/2014/06/DataModel-Relations1.png)<br />
We connect lines between tables to show relationships.  In some cases an entry in one table can be related to more than one entry in another.  This is called a one-to-many relationship.  In our example there are many employees in on department; therefore, we show a many-to-one relationship.

A many-to-one relationship is similar to a one-to-many relationship, this difference is in the point-of-view you take when naming the relationship.  I think most people speak of  one-to-many relationship more often.

Sometimes a there may not be an entry in a table, so technically speaking the you could have zero or one to many, but that gets hard to say, so when speaking in general terms, most people say “one-to-many.”  However, when you want to get precise,   you can use notation to specify the cardinality of a relationship.


---
- [BACK (Main Page)](./README.md)
---



