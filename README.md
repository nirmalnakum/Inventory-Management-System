# 🛒 E-Commerce Supply Chain & Inventory Management System

A comprehensive **Database Management System (DBMS)** project designed to model and manage the complete workflow of an e-commerce platform.

The system handles product catalogs, product variants, vendors, warehouses, inventory, customers, shopping carts, wishlists, orders, payments, shipments, purchase orders, reviews, coupons, and return/refund operations.

The database is implemented using **PostgreSQL** and designed with proper relationships, integrity constraints, normalization, and real-world SQL queries.

---

## 📌 Project Overview

Modern e-commerce platforms require efficient management of multiple interconnected operations such as:

- Product and category management
- Product variants
- Vendor and supplier management
- Warehouse management
- Inventory tracking
- Customer management
- Shopping carts and wishlists
- Order processing
- Payment tracking
- Shipment tracking
- Coupon management
- Purchase orders
- Product reviews
- Returns and refunds
- Sales and revenue analysis

This project provides a structured relational database solution for managing these operations efficiently.

---

## 🛠️ Tech Stack

- **Database:** PostgreSQL
- **Language:** SQL
- **Database Design:** ER Model and Relational Model
- **Normalization:** Boyce-Codd Normal Form (BCNF)
- **Tools:** pgAdmin / PostgreSQL CLI

---

## 🗃️ Major Database Entities

The database contains the following major entities:

| Entity | Purpose |
|---|---|
| Category | Stores hierarchical product categories |
| Product | Stores product information |
| ProductVariant | Manages product variations such as size and color |
| Vendor | Stores supplier information |
| VendorProduct | Connects vendors with product variants and selling prices |
| Warehouse | Stores warehouse details and capacity |
| Inventory | Tracks product stock across warehouses |
| PurchaseOrder | Stores purchase orders placed with vendors |
| PurchaseOrderItem | Stores products included in purchase orders |
| Customer | Stores customer account information |
| Address | Stores delivery addresses |
| CustomerAddress | Maps customers to multiple addresses |
| Cart | Stores customer shopping carts |
| CartItem | Stores products added to carts |
| WishList | Stores customer wishlists |
| WishListItem | Stores products saved in wishlists |
| Order | Stores customer orders |
| OrderItem | Stores individual items of an order |
| Payment | Tracks payment transactions |
| Shipment | Tracks shipment and delivery details |
| Coupon | Stores promotional coupon information |
| Review | Stores customer product reviews |
| ReturnRefund | Handles return and refund requests |

---

## 🔗 Database Relationships

Some important relationships implemented in the database are:

- A **Category** can contain multiple Products.
- A Category can also have a parent Category.
- A **Product** can have multiple Product Variants.
- A **Vendor** can supply multiple Product Variants.
- A Product Variant can be supplied by different Vendors.
- A **Warehouse** stores multiple inventory records.
- A **Customer** can have multiple Addresses.
- A Customer owns one Cart containing multiple Cart Items.
- A Customer can create multiple Wishlists.
- A Customer can place multiple Orders.
- An Order can contain multiple Order Items.
- An Order can have associated Payment and Shipment records.
- Customers can write Reviews for purchased products.
- Order Items can be associated with Return and Refund requests.

---

## ✨ Key Features

### 📦 Inventory Management

- Track product stock across multiple warehouses.
- Store bin locations for warehouse organization.
- Maintain reorder levels for products.
- Identify low-stock products.
- Calculate remaining warehouse capacity.

### 🏭 Vendor & Procurement Management

- Store vendor contact and GST information.
- Track vendor ratings.
- Manage products supplied by each vendor.
- Store vendor-specific selling prices.
- Manage purchase orders and purchase order items.
- Track procurement status and expected delivery dates.

### 🛍️ Customer Shopping System

- Customer registration and account information.
- Multiple customer delivery addresses.
- Default address management.
- Shopping cart management.
- Wishlist management.
- Product reviews and ratings.

### 📑 Order Management

- Customer order creation.
- Multiple products per order.
- Order status tracking.
- Coupon application.
- Payment tracking.
- Shipment and courier tracking.

### 💳 Payment Management

The system tracks:

- Payment gateway
- Transaction reference
- Payment amount
- Payment status
- Payment timestamp

Supported payment states include:

- Pending
- Success
- Failed
- Refunded

### 🚚 Shipment Management

The shipment module manages:

- Courier partner
- Tracking number
- Estimated delivery date
- Dispatch date
- Shipment status
- Source warehouse
- Inventory reference

### 🔄 Return & Refund Management

The system supports:

- Return requests
- Return reasons
- Refund amount tracking
- Request dates
- Refund status management

---

## 📊 SQL Query Scenarios

The project contains real-world SQL queries grouped into different business scenarios.

### 1. Customer Shopping Behavior

Queries include:

- Customer wishlist details
- Customer cart contents and cart value
- Customers with wishlist items but no orders
- Customer default delivery addresses

### 2. Order Management

Queries include:

- Complete order details
- Delivered order tracking
- Pending or failed payments
- Revenue grouped by order status
- Coupon discount calculation

### 3. Inventory & Warehouse Management

Queries include:

- Warehouse stock utilization
- Remaining warehouse capacity
- Products below reorder level
- Complete inventory listing

### 4. Vendor & Purchase Order Management

Queries include:

- Purchase orders with vendor and product details
- Pending and shipped purchase orders
- Top-rated vendors
- Number of variants supplied by each vendor

### 5. Sales & Revenue Analysis

Queries include:

- Revenue by product category
- Top-spending customers
- Payment gateway-wise collection
- Best-selling products
- Coupon usage analysis

### 6. Return & Refund Analysis

Queries include:

- Customer return request details
- Total refunded amount
- Returns grouped by reason
- Approved refunds awaiting processing

### 7. Product & Review Analysis

Queries analyze customer ratings and reviews to understand product performance and customer satisfaction.

---

## 🧮 Database Normalization

The database schema has been analyzed using **Boyce-Codd Normal Form (BCNF)** principles.

For every non-trivial functional dependency:

> X → Y

the determinant **X is a superkey** of the corresponding relation.

The normalization process helps reduce:

- Data redundancy
- Update anomalies
- Insert anomalies
- Delete anomalies

The project includes a separate document containing the BCNF proof for the database relations.

---

## 🔐 Data Integrity

The database uses several mechanisms to maintain data consistency.

### Primary Keys

Each major entity contains a unique primary key.

Examples:

- `ProductID`
- `VariantID`
- `VendorID`
- `WarehouseID`
- `CustomerID`
- `OrderID`
- `PaymentID`
- `ShipmentID`

### Foreign Keys

Foreign key constraints maintain relationships between tables.

Examples:

- Product → Category
- ProductVariant → Product
- VendorProduct → Vendor
- VendorProduct → ProductVariant
- Inventory → Warehouse
- Inventory → ProductVariant
- Order → Customer
- OrderItem → Order
- Payment → Order
- Shipment → Order

### CHECK Constraints

The database validates important business rules such as:

- Vendor rating between 0 and 5
- Positive product selling prices
- Non-negative inventory quantity
- Positive order item quantity
- Valid order status
- Valid payment status
- Valid shipment status
- Review rating between 1 and 5

### UNIQUE Constraints

Unique constraints are used for attributes such as:

- Product SKU
- Variant SKU
- Customer email
- Customer phone number
- Vendor GST number
- Payment transaction reference
- Coupon code
- Shipment tracking number

---

## 📁 Suggested Repository Structure

```text
Ecommerce-Supply-Chain-DBMS/
│
├── README.md
│
├── sql/
│   ├── ddl.sql
│   ├── insert_data.sql
│   └── queries.sql
│
├── diagrams/
│   ├── ER_Diagram.pdf
│   └── Relational_Schema.pdf
│
└── documentation/
    └── BCNF_Proof.pdf
