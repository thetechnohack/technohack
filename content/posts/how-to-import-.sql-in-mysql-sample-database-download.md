+++
title = "How to Import *.sql Files in MySQL + Download Sample Tables & Database"
date = "2021-03-04"
description = "How to import .sql files in mysql command line. Free sample database download for practicing. Importing .sql files is an easy task you can easily do that. You just need the SOURCE statement and you are all set. "
tags = [
    "termux",
    "mariadb",
    "database",
    "mysql",
    "android",
    "sql"
]
cover = "https://res.cloudinary.com/morphy/image/upload/v1612159107/termux-mariadb/mariadb-img_o9mksp.jpg"
+++

In this tutorial we will see how to import .sql (tables or databases) files in MySQL-CLI.

MariaDB and MySQL have some differences and similarities although both are commonly known as MySQL. We will use MariaDB as our database management system throughout this tutorial.

You can see below how the MySQL and MariaDB prompts look like :

- MySQL prompt:

```
mysql>
```

- MariaDB prompt:

```
MariaDB [(none)]>
```

## What is a .sql file ?

The \*.sql extension is a file which contains some sql statements like — Create - Select - Insert - View etc. in a proper order to perform the creation of databases and tables. It is also known as "dump" because it is basically a mysql export.

## Creating Database

First of all, we have to create a database in which we can import sql tables.

Let's create a database named "_test_" using the CREATE DATABASE statement :

```
MariaDB [(none)]> CREATE DATABASE test;
```

Select the "_test_" database as the default database using USE statement :

```
MariaDB [(none)]> USE test;
```

<br>

## Importing \*.sql Sample Tables

We have two sample tables here. We will import them in our "_test_" database :

- event table
- pet table

### Event table

Download and extract the following zip file in your working directory : <a href="https://github.com/thetechnohack/files/raw/main/mysql%20samples/event-table.zip" class="buttonDownload">Download event-table.zip</a>

You can see that there are two files in event-table folder :

```
event-table
├── cr_event_tbl.sql
└── event.txt
```

But why do we need two separate files ??

It is because the sql file here is only containing the table structure and the text file is holding the values for that table structure.
But it is not necessary to use two different files, we can also hold table structure and values together in a sql file.

1. **cr_event_tbl.sql**

This file contains the table structure or table format.

Import this file using the SOURCE statement as shown below :

```
MariaDB [test]> SOURCE cr_event_tbl.sql
```

It will create an empty table "_event_" :

```
MariaDB [test]> SHOW TABLES;
+---------------------+
| Tables_in_test      |
+---------------------+
| event               |
+---------------------+
1 row in set (0.010 sec)
```

2. **event.txt**

This file contains the data (values) for event table. We need to load this data in event table.

Use the below statement to load the event.txt in event table :

```
MariaDB [test]> LOAD DATA LOCAL INFILE 'event.txt' INTO TABLE event;
```

Now we have the complete table. You can see the complete table using the SELECT statement:

```
MariaDB [test]> SELECT * FROM event;
+----------+------------+----------+-----------------------------+
| name     | date       | type     | remark                      |
+----------+------------+----------+-----------------------------+
| Fluffy   | 1995-05-15 | litter   | 4 kittens, 3 female, 1 male |
| Buffy    | 1993-06-23 | litter   | 5 puppies, 2 female, 3 male |
| Buffy    | 1994-06-19 | litter   | 3 puppies, 3 female         |
| Chirpy   | 1999-03-21 | vet      | needed beak straightened    |
| Slim     | 1997-08-03 | vet      | broken rib                  |
| Bowser   | 1991-10-12 | kennel   | NULL                        |
| Fang     | 1991-10-12 | kennel   | NULL                        |
| Fang     | 1998-08-28 | birthday | Gave him a new chew toy     |
| Claws    | 1998-03-17 | birthday | Gave him a new flea collar  |
| Whistler | 1998-12-09 | birthday | First birthday              |
+----------+------------+----------+-----------------------------+
10 rows in set (0.012 sec)
```

### Pet table

Download and extract the following zip file in your working directory : <a href="https://github.com/thetechnohack/files/raw/main/mysql%20samples/pet-table.zip" class="buttonDownload">Download pet-table.zip</a>

Follow the same procedure as we done above.

Folder structure of pet-table :

```
pet-table
├── cr_pet_tbl.sql
└── pet.txt
```

1. **cr_pet_tbl.sql**

Importing _cr_pet_tbl.sql_ in "_test_" database :

```
MariaDB [test]> SOURCE cr_pet_tbl.sql
```

This will create a new empty table as name "_pet_" :

```
MariaDB [test]> SHOW TABLES;
+---------------------+
| Tables_in_test      |
+---------------------+
| event               |
| pet                 |
+---------------------+
2 rows in set (0.010 sec)
```

2. **pet.txt**

Load data form pet.txt in pet table :

```
MariaDB [test]> LOAD DATA LOCAL INFILE 'pet.txt' INTO TABLE pet;
```

Print the entire table using SELECT statement :

```
MariaDB [test]> SELECT * FROM pet;
+----------+--------+---------+------+------------+------------+
| name     | owner  | species | sex  | birth      | death      |
+----------+--------+---------+------+------------+------------+
| Fluffy   | Harold | cat     | f    | 1993-02-04 | NULL       |
| Claws    | Gwen   | cat     | m    | 1994-03-17 | NULL       |
| Buffy    | Harold | dog     | f    | 1989-05-13 | NULL       |
| Fang     | Benny  | dog     | m    | 1990-08-27 | NULL       |
| Bowser   | Diane  | dog     | m    | 1979-08-31 | 1995-07-29 |
| Chirpy   | Gwen   | bird    | f    | 1998-09-11 | NULL       |
| Whistler | Gwen   | bird    | NULL | 1997-12-09 | NULL       |
| Slim     | Benny  | snake   | m    | 1996-04-29 | NULL       |
+----------+--------+---------+------+------------+------------+
8 rows in set (0.011 sec)
```

## Importing Sample .sql database

Here, we have a .sql database dump, which means you don't need to create an empty table first and then import data into it. It will automatically create a database with some sample tables in it.

Download and extract the following zip file in your working directory : <a href="https://github.com/thetechnohack/files/raw/main/mysql%20samples/mydb.zip" class="buttonDownload">Download database</a>

Now just use the SOURCE statement :

```
MariaDB [(none)]> SOURCE mysqlsampledatabase.sql;
```

It will create a database, **classicmodels** with some tables in it.

Select the **classicmodels** as default database :

```
MariaDB [(none)]> USE classicmodels;
```

There are different tables for practicing MySQL statements :

```
MariaDB [classicmodels]> SHOW TABLES;
+-------------------------+
| Tables_in_classicmodels |
+-------------------------+
| customers               |
| employees               |
| offices                 |
| orderdetails            |
| orders                  |
| payments                |
| productlines            |
| products                |
+-------------------------+
8 rows in set (0.001 sec)
```

Hope you liked this tutorial.
Comment your suggestions and queries. **We always appreciate your feedback 😊**

<br>

<style>
.buttonDownload {
	display: inline-block;
	position: relative;
	padding: 10px 25px;
   background-color: #4CC713;
   color: white;
   font-family: sans-serif;
	text-decoration: none;
	font-size: 0.9em;
	text-align: center;
	text-indent: 15px;
   border-radius: 8px;
   outline: none;
}

.buttonDownload:hover {
	background-color: #333;
	color: white;
}

.buttonDownload:before, .buttonDownload:after {
	content: ' ';
	display: block;
	position: absolute;
	left: 15px;
	top: 52%;
}

/* Download box shape  */
.buttonDownload:before {
	width: 10px;
	height: 2px;
	border-style: solid;
	border-width: 0 2px 2px;
}

/* Download arrow shape */
.buttonDownload:after {
	width: 0;
	height: 0;
	margin-left: 3px;
	margin-top: -7px;
  
	border-style: solid;
	border-width: 4px 4px 0 4px;
	border-color: transparent;
	border-top-color: inherit;
	
	animation: downloadArrow 2s linear infinite;
	animation-play-state: paused;
}

.buttonDownload:hover:before {
	border-color: #4CC713;
}

.buttonDownload:hover:after {
	border-top-color: #4CC713;
	animation-play-state: running;
}

/* keyframes for the download icon anim */
@keyframes downloadArrow {
	/* 0% and 0.001% keyframes used as a hackish way of having the button frozen on a nice looking frame by default */
	0% {
		margin-top: -7px;
		opacity: 1;
	}
	
	0.001% {
		margin-top: -15px;
		opacity: 0;
	}
	
	50% {
		opacity: 1;
	}
	
	100% {
		margin-top: 0;
		opacity: 0;
	}
}
</style>
