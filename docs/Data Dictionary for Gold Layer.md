# Data Dictionary for Gold Layer

---

## Overview

---

The Gold Layer is the Business-level data representation, structured to support analytical and reporting use cases. it consists of dimension tables and fact tables for specific. business metrics.

---

### 1. gold.dim_customers

- Purpose: Stores Customer details enriched with demographic and geographic data.
- columns:

| **Column name** | **Data Type** | **Description** |
| --- | --- | --- |
| customer_key | INT | Surrogate Key uniquely identifying each customer in the dimension table |
| customer_id | INT | Uniquely numerical identifier assigned to each customer |
| Customer_number | NVACHAR(50) | Alphanumeric identifier representing the customer, used for tracking and referencing. |
| first_name | NVACHAR(50) | The customer’s first name, as recorded in the system.  |
| last_name | NVACHAR(50) | The customer’s last name or family name |
| country | NVACHAR(50) | the country of residence for the customer |
| marital_status | NVACHAR(50) | The marital status of the customer(e.g., ‘Married’ , ‘Single’) |
| gender | NVACHAR(50) | The gender of the customer (e.g., ‘Male’ , ‘Female’ , ‘unkown’). |
| birthdate | DATE | the date of birth of the customer, formatted as YYYY-MMDD (eg., 1971-10-06). |
| create_date | DATE | The date and time when the customer record was created in the system |

### 2. gold.dim_products

 Purpose: Provides information about the products and their attributes 

- purpose: provides information about the products and their attributes.
- columns:

| **Column name** | **Data Type** | **Description** |
| --- | --- | --- |
| product_key  | INT | Surrogate Key uniquely identifying each product record in the production dimension table. |
| product_id | INT | A unique identifier assigned to the product for internal tracking and referencing |
| product_number | NVACHAR(50) | A structured alphanumeric code representing the product, often used for categorization or inventory. |
| product_name | NVACHAR(50) | Descriptive name of the product, including key details such as type, colour, and size. |
| category_id | NVACHAR(50) | A unique identifier for the product’s category, linking to its high-level classification.  |
| category | NVACHAR(50) | The broader classification of the product(e.g BIkes Components) to the group related items |
| subcategory  | NVACHAR(50) | A more detailed classification of the product within the category, such as product type |
| maintainance_required | NVACHAR(50) | Indicates whether the product requires maintainance (e.g. ‘Yes’ , ‘No’)  |
| cost | INT  | The cost or base price of the product, measured in monetary units.  |
| product_line  | NVARCHAR(50) | The specific product line or series to which the produc belongs (e.g., Road, Mountain) |
| Start_date | DATE | The date when the product became available for sale or use, stored in  |

### 3. gold.fact_sales

- purpose: Stores transactional sales data for analytical purposes.
- columns:

| **Column name** | **Data Type** | **Description** |
| --- | --- | --- |
| order_number | NVARCHAR(50) | A unique alphanumeric identifier for each sales order(e.g, ‘SO54496’). |
| product_key | INT | Surrogate key linking the order to the order to product dimension table.  |
| customer_key | INT | Surrogate key linking the order to the customer dimension table. |
| order_date  | DATE | the date when he order was placed |
| shipping_date | DATE | the date when the order was shipped to the customer.  |
| due_date | DATE  | the date when the payment was due |
| sales_amount | INT  | The total monetary value of the sale for the line item, in whole currency units. (e.g. 25) |
| quantity  | INT  | The number of units of the product ordered for the line item (e.g., 1). |
| price  | INT | The price per unit of the product for the line item, in the whole currency units (e.g., 25). |