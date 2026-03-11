# DBMS_2-semester-final-project-
SQL database project for a clothing store featuring 5 tables, CRUD operations, joins, subqueries, and aggregate functions.
# 👗 Clothing Store Database Management System

A comprehensive SQL database project for managing a clothing retail store's operations including products, customers, orders, and inventory.

## 📋 Table of Contents
- [Overview](#overview)
- [Database Schema](#database-schema)
- [Technologies Used](#technologies-used)
- [Features](#features)
- [SQL Concepts Covered](#sql-concepts-covered)
- [Installation](#installation)
- [Usage](#usage)
- [Sample Queries](#sample-queries)
- [Project Structure](#project-structure)

## 📝 Overview
This project implements a fully functional relational database for a clothing store. It demonstrates fundamental and advanced database concepts through practical implementation of real-world business scenarios.

## 🗄️ Database Schema

### Tables Structure

```sql
1. categories
   - category_id (PK)
   - category_name
   - description

2. products  
   - product_id (PK)
   - product_name
   - price
   - quantity
   - discount_percent
   - category_id (FK)

3. customers
   - customer_id (PK)
   - name
   - phone
   - email

4. orders
   - order_id (PK)
   - customer_id (FK)
   - order_date

5. order_details
   - order_detail_id (PK)
   - order_id (FK)
   - product_id (FK)
   - quantity
   - total_price
```

### Entity Relationship Diagram
```
categories ────< products
                    │
                    │
customers ────< orders ────< order_details >─── products
```

## 💻 Technologies Used
- **PostgreSQL** - Primary database management system
- **SQL** - Structured Query Language

## ✨ Features

### Business Features
- Product categorization (Unstitched, Ready to Wear, Accessories, Fragrances)
- Inventory management with quantity tracking
- Discount management system
- Customer information management
- Order processing with automatic date tracking
- Sales calculation and reporting

### Technical Features
- Referential integrity with foreign keys
- Unique constraints on customer emails
- Default values for dates and discounts
- Serial auto-incrementing primary keys

## 📚 SQL Concepts Covered

### 1. **Data Definition Language (DDL)**
- CREATE TABLE with constraints
- PRIMARY KEY and FOREIGN KEY relationships
- SERIAL auto-increment
- DEFAULT values
- UNIQUE constraints

### 2. **Data Manipulation Language (DML)**
- INSERT statements for sample data
- UPDATE operations for inventory management
- DELETE operations for data removal

### 3. **Basic Queries**
- SELECT statements
- DISTINCT values
- WHERE clause filtering

### 4. **Aggregate Functions**
- COUNT() for record counting
- MIN() and MAX() for price ranges
- AVG() for average calculations
- SUM() for total sales

### 5. **Advanced Clauses**
- GROUP BY for data grouping
- HAVING for group filtering
- ORDER BY for sorting
- BETWEEN for range filtering
- LIKE for pattern matching
- AND/OR/NOT logical operators

### 6. **Joins**
- INNER JOIN for matching records
- LEFT JOIN for all products
- RIGHT JOIN for all categories

### 7. **Subqueries**
- Nested queries with IN operator
- Comparison with aggregate results
- Correlated subqueries

## 🔧 Installation

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/clothing-store-dbms.git
cd clothing-store-dbms
```

2. **Install PostgreSQL**
   - Download from [postgresql.org](https://www.postgresql.org/download/)
   - Follow installation instructions for your OS

3. **Create database**
```sql
CREATE DATABASE clothing_store;
```

4. **Run the SQL script**
```bash
psql -d clothing_store -f database_setup.sql
```

## 📖 Usage

### Basic Operations

**View all products:**
```sql
SELECT * FROM products;
```

**Check customer orders:**
```sql
SELECT o.order_id, c.name, o.order_date
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id;
```

**Calculate total sales:**
```sql
SELECT SUM(total_price) FROM order_details;
```

**Find discounted products:**
```sql
SELECT product_name, price, discount_percent
FROM products
WHERE discount_percent > 0;
```

## 📊 Sample Queries

### Business Intelligence Queries

1. **Top selling products**
```sql
SELECT p.product_name, SUM(od.quantity) as total_sold
FROM products p
JOIN order_details od ON p.product_id = od.product_id
GROUP BY p.product_name
ORDER BY total_sold DESC;
```

2. **Customer purchase history**
```sql
SELECT c.name, COUNT(o.order_id) as order_count, SUM(od.total_price) as total_spent
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
JOIN order_details od ON o.order_id = od.order_id
GROUP BY c.name;
```

3. **Category-wise sales**
```sql
SELECT cat.category_name, SUM(od.total_price) as revenue
FROM categories cat
JOIN products p ON cat.category_id = p.category_id
JOIN order_details od ON p.product_id = od.product_id
GROUP BY cat.category_name;
```

## 📁 Project Structure
```
clothing-store-dbms/
│
├── README.md
├── database_setup.sql
├── sample_data.sql
├── queries/
│   ├── basic_queries.sql
│   ├── aggregate_functions.sql
│   ├── joins.sql
│   └── subqueries.sql
└── documentation/
    ├── schema_diagram.png
    └── project_report.pdf
```

## 🎯 Learning Outcomes
- Understanding relational database design principles
- Implementing real-world business rules in SQL
- Mastering various SQL query types and clauses
- Working with foreign keys and referential integrity
- Performing data analysis using aggregate functions
- Combining tables using different join types

## 🤝 Contributing
Contributions, issues, and feature requests are welcome! Feel free to check the issues page.

## 📝 License
This project is licensed under the MIT License - see the LICENSE file for details.

## 👤 Author
**Arfa Arfan**
- Roll No: 2024-csre-032
- Class: Computer Science
- Institution: UVAS Ravi Campus

## 🙏 Acknowledgments
- Prof. Anees J. for guidance and supervision
- PostgreSQL documentation and community

---

