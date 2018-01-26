sudo apt install mysql-server 
================================
NOT NULL - Ensures that a column cannot have a NULL value</br>
UNIQUE - Ensures that all values in a column are different</br>
PRIMARY KEY - A combination of a NOT NULL and UNIQUE. Uniquely</br> identifies each row in a table</br>
FOREIGN KEY - Uniquely identifies a row/record in another table</br>
CHECK - Ensures that all values in a column satisfies a specific condition</br>
DEFAULT - Sets a default value for a column when no value is specified</br>
INDEX - Used to create and retrieve data from the database very quickly</br>

usage(set default to run against the schema)
=============
**create schema**
- create shcema 'name';

**load data**
- load data local infile '/home/cooper/Documents/test.csv'
- into table _schema_name._table_name
- fields terminated by ','
- lines terminated by '!'
- ignore 0 lines
- (@col1,@dummy,@col2)
- set column_1 = @col1, column_2 = @col2;

**view table**
- select * from schema_name.table_name

**create table**
- need to set default 
- create table table_name (
	column_1 VARCHAR(45),
	column_2 INT
);

**join different table**
- SELECT Orders.OrderID as 'new name', 
	Customers.CustomerName, Shippers.ShipperName
- FROM Orders
- INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID
- INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID
- where table_name.column_name like '%something%';
- P.S. =:Equal; <>:Not equal. Note: In some versions of SQL this operator may be written as !=; >:Greater than; <:Less than; >=:Greater than or equal; <=:Less than or equal; BETWEEN:Between an inclusive range; LIKE:Search for a pattern; IN:To specify multiple possible values for a column

