🛒 Inventory Management System
This project demonstrates a simple inventory management system with a relational database structure, utilizing tables for suppliers, products, and inventory. The database allows for the storage and management of product details, supplier information, and inventory stock levels.

🗂️ Database Structure
The database consists of the following tables:

1. Suppliers 🏢
This table stores information about the suppliers that provide products.

Column Name	Data Type	Description
supplier_id	INT (Primary Key)	Unique identifier for each supplier
supplier_name	VARCHAR(100)	Name of the supplier
contact_info	VARCHAR(100)	Contact information (e.g., email)
2. Products 📦
This table stores details about the products available in the inventory.

Column Name	Data Type	Description
product_id	INT (Primary Key)	Unique identifier for each product
product_name	VARCHAR(100)	Name of the product
category	VARCHAR(50)	Category of the product
supplier_id	INT (Foreign Key)	Reference to the supplier table
cost_price	DECIMAL(10,2)	Cost price of the product
selling_price	DECIMAL(10,2)	Selling price of the product
reorder_level	INT	Minimum stock level for reorder
3. Inventory 📊
This table manages the stock levels of products in the warehouse.

Column Name	Data Type	Description
inventory_id	INT (Primary Key)	Unique identifier for each inventory record
product_id	INT (Foreign Key)	Reference to the product table
quantity	INT	Number of items in stock
last_updated	TIMESTAMP	The timestamp when the stock was last updated
🔑 Sample SQL Queries
1. Create Database and Use It 📂
sql
Copy
CREATE DATABASE inventory_management;
USE inventory_management;
2. Create Tables 🛠️
sql
Copy
CREATE TABLE suppliers (
    supplier_id INT PRIMARY KEY AUTO_INCREMENT,
    supplier_name VARCHAR(100) NOT NULL,
    contact_info VARCHAR(100)
);

CREATE TABLE products (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    product_name VARCHAR(100) NOT NULL,
    category VARCHAR(50),
    supplier_id INT,
    cost_price DECIMAL(10,2) NOT NULL,
    selling_price DECIMAL(10,2) NOT NULL,
    reorder_level INT NOT NULL,
    FOREIGN KEY (supplier_id) REFERENCES suppliers(supplier_id)
);

CREATE TABLE inventory (
    inventory_id INT PRIMARY KEY AUTO_INCREMENT,
    product_id INT,
    quantity INT NOT NULL,
    last_updated TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (product_id) REFERENCES products(product_id)
);
3. Insert Sample Data ✍️
sql
Copy
INSERT INTO suppliers (supplier_name, contact_info)
VALUES
    ('Supplier A', 'supplier_a@example.com'),
    ('Supplier B', 'supplier_b@example.com'),
    ('Supplier C', 'supplier_c@example.com');

INSERT INTO products (product_name, category, supplier_id, cost_price, selling_price, reorder_level)
VALUES
    ('Product A', 'Electronics', 1, 100.00, 150.00, 10),
    ('Product B', 'Books', 2, 20.00, 30.00, 5),
    ('Product C', 'Clothing', 3, 50.00, 75.00, 20);

INSERT INTO inventory (product_id, quantity)
VALUES
    (1, 100),
    (2, 50),
    (3, 20);
4. Querying Data 🔍
To retrieve all suppliers:

sql
Copy
SELECT * FROM suppliers;
To retrieve all products:

sql
Copy
SELECT * FROM products;
To retrieve all inventory items:

sql
Copy
SELECT * FROM inventory;
🚀 Usage
Clone the repository to your local machine.
Import the SQL script into your MySQL or compatible database system.
Use the queries in the script to create the database, tables, and insert sample data.
Customize the database for your inventory management needs.
🛠️ Technologies Used
MySQL (or any relational database management system)
SQL
