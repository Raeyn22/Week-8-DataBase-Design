# Week-8-DataBase-Design

# 📚 Library Management System - MySQL Database

## 📌 Project Title
**Library Management System Database**  
*A complete relational database for managing library operations*

## 📝 Description
This project is a comprehensive MySQL database solution for library management systems. It handles all core library operations including:

- **Patron management** (member registration, membership tracking)
- **Catalog management** (books, authors, publishers)
- **Inventory control** (physical copies tracking)
- **Circulation** (checkouts, returns, reservations)
- **Financials** (fines and payments)
- **Staff and branch management**
- **Audit logging** for data integrity

The database features proper normalization, constraints, and relationships to ensure data consistency and support efficient queries.

## 🛠️ Setup Instructions

### Prerequisites
- MySQL Server (8.0+ recommended)
- MySQL Workbench or similar client (optional)

### Installation
1. **Create the database**:
   ```sql
   CREATE DATABASE library_management_system;
   USE library_management_system;
   ```

2. **Import the schema**:
   - Copy the entire SQL script from the provided file
   - Execute it in your MySQL client
   - OR use command line:
     ```bash
     mysql -u [username] -p library_management_system < library_schema.sql
     ```

3. **Verify installation**:
   ```sql
   SHOW TABLES;
   ```

## 🔗 ERD (Entity Relationship Diagram)
![Library Management System ERD](https://i.imgur.com/JQhG3Zm.png)  
*Visual representation of tables and relationships*

[View interactive ERD on dbdiagram.io](https://dbdiagram.io/d/64f1a5d002bd1c4a5e8a7a2a)

## 🏛️ Sample Data (Optional)
To populate with sample data, run:
```sql
-- Sample publishers
INSERT INTO publishers (name, address, phone, email, website)
VALUES 
('Penguin Random House', '1745 Broadway, New York, NY', '212-782-9000', 'info@penguinrandomhouse.com', 'www.penguinrandomhouse.com'),
('HarperCollins', '195 Broadway, New York, NY', '212-207-7000', 'contact@harpercollins.com', 'www.harpercollins.com');

-- Continue with other sample data...
```

## 📊 Sample Queries
```sql
-- Find all books checked out by a member
SELECT b.title, l.checkout_date, l.due_date 
FROM loans l
JOIN book_copies bc ON l.copy_id = bc.copy_id
JOIN books b ON bc.book_id = b.book_id
WHERE l.member_id = 1 AND l.status = 'Active';

-- Calculate total fines for a member
SELECT SUM(amount) AS total_fines 
FROM fines 
WHERE member_id = 1 AND status = 'Pending';
```

## 📜 License
MIT License - Free for educational and personal use
