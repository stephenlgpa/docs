# SQL Basics

## Introduction

Databases are created from tables, made up of rows (records), made up of columns of data (fields). To interact with a database, we send it a series of commands (a query) in Structured Query Language (SQL).

SQL commands are not case-sensitive, but database entities (i.e. schemas, tables, and columns) are! By convention, commands are written in uppercase.

Tablenames and Fieldnames should be always surrounded by backticks to force MySQL to treat them as names and not commands. (This is not actually necessary, but stops MySQL becoming confused if a tablename is named after a command.)

## Data Types

3 main types:

- numbers
- text
- date/time

## Create a Database (Schema)

```
CREATE SCHEMA databasename;
```

- substitute 'databasename' for the name of the database, with case-sensitivity.

## Create a Table

```
CREATE TABLE `databasename`.`tablename`
	(`field1` TYPE OPTIONS,
	`field2` TYPE OPTIONS,
	...,
	PRIMARY KEY (`primaryKeyFieldName`));
```

- \`databasename\` should already exist!
- \`tablename\` is the new table to create
- **TYPE** is the datatype of the field.
	- INT: integer
	- TEXT: text
	- DATE: date
	- Text strings are delimited by 'single' or "double" quotes.
	- Dates are also entered as strings ('yyyy-mm-dd' or "yyyy-mm-dd).
	- To escape a single/double quote, use the backslash (\\) before the quote.
- **OPTIONS**: depends on the type
	- INT
		- NULL/NOT NULL (can be no value, must have a value)
		- AUTO_INCREMENT (automatically fills with the next higher integer)
- **PRIMARY KEY**: the field to uniquely identify each row of data.
 
## Deleting a Table (DROP)

```
DROP `tablename`;
```

- Be careful! This command is permanent!

## Adding Data (INSERT)

```
INSERT INTO tablename SET
	column1Name = value1,
	column2Name = value2
	... ;
```
		
OR
		
```
INSERT INTO tablename
	(column1Name, column2Name, ...)
	VALUES (value1, value2, ...);
```

## Retrieving Data (SELECT)

### SELECT all rows

	SELECT * FROM `tablename`;

- _\*_ is the wildcard character

### SELECT Specific Columns

	SELECT `column1`, `column2` FROM `tablename`;

## Other Functions

### LEFT( )

	SELECT LEFT(`textColumn1`, 20) FROM `tablename`;

LEFT( ) trims text to a specified length.

### COUNT( )

	SELECT COUNT(`column1`) FROM `tablename`;

## SELECTing specific attributes - WHERE

WHERE allows you to SELECT based on criteria (narrows down the selected results).

	SELECT `column1` FROM `tablename` WHERE `column3` [someConditional];

The conditional could be, for example:

	... WHERE `column3` > "2018-06-01";

This returns results where the dates in column3 are later than my birthday in 2018.










