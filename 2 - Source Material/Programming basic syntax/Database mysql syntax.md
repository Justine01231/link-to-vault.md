
### 🗃️ **Database Management**

**Show all databases:**

SHOW DATABASES;

CREATE DATABASE mydb;

**Select a database to work with:**

USE mydb;
DROP DATABASE mydb;


### 📄 **Table Management**

 **Show all tables in the current database:**
 SHOW TABLES;

Create a new table:
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100)
);

Describe a table (structure of the table):
DESCRIBE users;

delete table command
DROP TABLE users;


