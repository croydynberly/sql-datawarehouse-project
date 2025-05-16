# Data Catalog for Gold Layer

## Overview
The **Gold Layer** is the business-level data representation, structured to support analytical and reporting use cases. It consists of dimension tables and fact tables for specific business metrics.

---

## 1. gold.dim_customers

**Purpose**: Stores customer details enriched with demographic and geographic data.

| Column Name       | Data Type       | Description                                                                 |
|-------------------|------------------|-----------------------------------------------------------------------------|
| customer_key      | INT              | Surrogate key uniquely identifying each customer record in the dimension.  |
| customer_id       | INT              | Unique numerical identifier assigned to each customer.                     |
| customer_number   | NVARCHAR(50)     | Alphanumeric identifier representing the customer.                         |
| first_name        | NVARCHAR(50)     | The customer's first name.                                                 |
| last_name         | NVARCHAR(50)     | The customer's last name or family name.                                   |
| country           | NVARCHAR(50)     | Country of residence (e.g., 'Australia').                                  |
| marital_status    | NVARCHAR(50)     | Marital status (e.g., 'Married', 'Single').                                |
| gender            | NVARCHAR(50)     | Gender (e.g., 'Male', 'Female', 'n/a').                                    |
| birthdate         | DATE             | Date of birth (e.g., 1971-10-06).                                          |
| create_date       | DATE             | When the customer record was created.                                      |

---

## 2. gold.dim_products

**Purpose**: Provides information about the products and their attributes.

| Column Name         | Data Type       | Description                                                              |
|---------------------|------------------|--------------------------------------------------------------------------|
| product_key         | INT              | Surrogate key identifying each product.                                 |
| product_id          | INT              | Unique identifier for the product.                                       |
| product_number      | NVARCHAR(50)     | Structured alphanumeric code used for categorization.                   |
| product_name        | NVARCHAR(50)     | Descriptive name including type, color, and size.                        |
| category_id         | NVARCHAR(50)     | Identifier for the product's category.                                   |
| category            | NVARCHAR(50)     | High-level classification (e.g., Bikes, Components).                     |
| subcategory         | NVARCHAR(50)     | Detailed classification of the product.                                  |
| maintenance_required| NVARCHAR(50)     | Indicates if maintenance is needed ('Yes' / 'No').                       |
| cost                | INT              | Base price in currency units.                                            |
| product_line        | NVARCHAR(50)     | Product line (e.g., Road, Mountain).                                     |
| start_date          | DATE             | When the product became available.                                       |

---

## 3. gold.fact_sales

**Purpose**: Stores transactional sales data for analytical purposes.

| Column Name    | Data Type       | Description                                                         |
|----------------|------------------|---------------------------------------------------------------------|
| order_number   | NVARCHAR(50)     | Unique identifier for each sales order (e.g., 'SO54496').          |
| product_key    | INT              | Foreign key linking to the product dimension.                       |
| customer_key   | INT              | Foreign key linking to the customer dimension.                      |
| order_date     | DATE             | Date when the order was placed.                                     |
| shipping_date  | DATE             | Date when the order was shipped.                                    |
| due_date       | DATE             | Payment due date.                                                   |
| sales_amount   | INT              | Total value of the sale.                                            |
| quantity       | INT              | Units of the product ordered.                                       |
| price          | INT              | Price per unit of the product.                                      |
