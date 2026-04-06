# 🛍️ Instagram Thrift & Handmade Store – ER Diagram

## 📌 Project Overview

This project presents a well-structured **Entity-Relationship (ER) Diagram** for a small but growing Instagram-based business that sells **thrifted fashion items** and **handmade products**.

Initially, orders are managed through Instagram DMs and WhatsApp, but as the business grows, a proper database system becomes essential to manage:

* Products
* Inventory
* Customer details
* Orders
* Payments
* Shipping

---

## 🔗 ER Diagram Link

👉 https://app.eraser.io/workspace/VFUtN5pB1CfID8LEIpQh

---

## 🖼️ ER Diagram Screenshot

![ER Diagram](./diagram/er-diagram.png)

> 📌 Note: Make sure your screenshot file is placed inside the `/diagram` folder with the name **er-diagram.png**

---

## 🎯 Objectives

The goal of this database design is to:

* Efficiently manage **both thrift and handmade products**
* Track **inventory (single-piece vs multiple units)**
* Maintain **customer and order history**
* Handle **payments and shipping status**
* Support **scalability as business grows**

---

## 🧠 Business Understanding

This is not a typical e-commerce system. The design carefully considers:

### 🧥 Thrift Products

* Usually **unique (only one piece available)**
* Includes:

  * Condition (new, like-new, good, fair)
  * Brand
  * Source details

### 🧶 Handmade Products

* Can have **multiple units (batch production)**
* Includes:

  * Custom or repeatable designs
  * Bulk inventory support

---

## 🧩 Core Entities

### 👤 Customer

* `customer_id (PK)`
* name
* phone
* email
* address

---

### 📦 Product

* `product_id (PK)`
* title
* description
* category
* price
* size
* color
* product_type (thrift / handmade)
* image_url
* is_active

---

### 🧥 Thrift_Item

* `product_id (PK, FK)`
* condition
* brand
* source_note

---

### 🧶 Handmade_Item

* `product_id (PK, FK)`
* material
* production_time
* batch_info

---

### 📊 Inventory

* `inventory_id (PK)`
* `product_id (FK)`
* quantity_available

---

### 🛒 Order

* `order_id (PK)`
* `customer_id (FK)`
* order_date
* total_amount
* order_status

---

### 📋 Order_Item (Junction Table)

* `order_item_id (PK)`
* `order_id (FK)`
* `product_id (FK)`
* quantity
* price_at_purchase

---

### 💳 Payment

* `payment_id (PK)`
* `order_id (FK)`
* payment_method
* payment_status
* payment_date

---

### 🚚 Shipping

* `shipping_id (PK)`
* `order_id (FK)`
* address
* courier_service
* tracking_number
* shipping_status
* delivery_date

---

## 🔗 Relationships & Cardinality

* One **Customer → Many Orders**
* One **Order → Many Order_Items**
* One **Product → Many Order_Items**
* One **Order → One Payment**
* One **Order → One Shipping**
* One **Product → One Inventory**
* One **Product → Either Thrift_Item OR Handmade_Item**

---

## ⚙️ Design Decisions

* Separate tables for **Thrift** and **Handmade** products
* Inventory handles both **single-piece and bulk products**
* Used **Order_Item** for many-to-many relationship
* Payment and Shipping are separated for clarity
* Database is **normalized and scalable**

---

## 📁 Repository Structure

```
/project-root
│
├── /diagram
│   └── er-diagram.png
│
├── README.md
```

---

## 📌 Conclusion

This ER diagram represents a **real-world growing Instagram business** and provides a scalable structure to manage:

* Unique thrift items
* Multi-unit handmade products
* Orders, payments, and deliveries

The design ensures smooth transition from a small manual system to a structured database-driven system.

---

## 🙌 Author

Peeyush Tiwari
Software Engineer | Tech Enthusiast

---
