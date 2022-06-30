MySQL Advanced
=

<h2>Create / Open / Delete Database</h2>


CREATE DATABASE DatabaseName;

CREATE DATABASE DatabaseName CHARACTER SET utf8;

USE DatabaseName;

DROP DATABASE DatabaseName;

ALTER DATABASE DatabaseName CHARACTER SET utf8;

<h2>Backup Database to SQL File</h2>

mysqldump -u Username -p dbNameYouWant > databasename_backup.sql

<h2>Create / Delete / Modify Table</h2>


CREATE TABLE table (field1 type1, field2 type2);

CREATE TABLE table (field1 type1, field2 type2, INDEX (field));

CREATE TABLE table (field1 type1, field2 type2, PRIMARY KEY (field1));

CREATE TABLE table (field1 type1, field2 type2, PRIMARY KEY (field1,field2));

CREATE TABLE table1 (fk_field1 type1, field2 type2, ...,

   FOREIGN KEY (fk_field1) REFERENCES table2 (t2_fieldA))

    [ON UPDATE|ON DELETE] [CASCADE|SET NULL]

CREATE TABLE table1 (fk_field1 type1, fk_field2 type2, ...,

  FOREIGN KEY (fk_field1, fk_field2) REFERENCES table2 (t2_fieldA, t2_fieldB))


<h2>Browsing</h2>

SHOW DATABASES;

SHOW TABLES;

SHOW FIELDS FROM table / DESCRIBE table;

SHOW CREATE TABLE table;

SHOW PROCESSLIST;

KILL process_number;

<h2>Reset Root Password</h2>


$ /etc/init.d/mysql stop

$ mysqld_safe --skip-grant-tables

$ mysql # on another terminal

mysql> UPDATE mysql.user SET password=PASSWORD('new_pass') WHERE user='root';

<h2>Users and Privileges</h2>

CREATE USER 'user'@'localhost';

GRANT ALL PRIVILEGES ON base.* TO 'user'@'localhost' IDENTIFIED BY 'password';

GRANT SELECT, INSERT, DELETE ON base.* TO 'user'@'localhost' IDENTIFIED BY 'password';

REVOKE ALL PRIVILEGES ON base.* FROM 'user'@'host'; -- one permission only

REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'user'@'host'; -- all permissions

FLUSH PRIVILEGES;