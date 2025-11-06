# 📦 Python Inventory Management System

This is a simple, standalone Inventory Management System built using **Python** and the **Tkinter** library for the graphical user interface (GUI). It uses an **SQLite** database to store and manage product, stock, and transaction data.

---

## ✨ Features

* **Sales/Billing Interface (`main.py`):**
    * Search for products by ID.
    * Add multiple products to a temporary "cart" with quantity and discount.
    * Calculates the total bill amount.
    * Calculates change to be given to the customer.
    * **Automatically updates stock** in the database upon generating a bill.
    * Records sales transactions (product, quantity, amount, date) in the database.
* **Add Products (`add-to-database.py`):**
    * A separate GUI tool to add new products to the inventory.
    * Calculates `total cost price`, `total selling price`, and `assumed profit` automatically.
    * Records product name, stock, cost price, selling price, vendor, and vendor phone number.
* **Update Products (`update.py`):**
    * A separate GUI tool to search for an existing product by ID.
    * Allows updating all product details (name, stock, price, vendor information).
* **Database Management:**
    * Uses a single SQLite file (`storedb.db`) for all data persistence.

---

## 🛠️ Requirements

To run this application, you need:

* **Python 3.x**
* **Tkinter** (usually included with standard Python installations)
* **SQLite3** (usually included with standard Python installations)

---

## 🚀 How to Run

1.  **Clone the repository** (once uploaded to GitHub).
2.  **Initialize the Database:** Before running the main application, you must create the necessary tables in the `storedb.db` file. You can run the setup SQL commands (see the Database Setup section below) or run `add-to-database.py` once to create the file.
3.  **Run the main application:**
    ```bash
    python main.py
    ```
4.  **Use the other scripts as needed:**
    ```bash
    python add-to-database.py   # To add new products
    python update.py            # To update existing products
    ```

---

## 💾 Database Setup (SQL Schema)

The application relies on two tables in the `storedb.db` file: `inventory` and `transactions`. You can use these SQL statements to initialize your database structure.

### 1. `inventory` Table

This table stores all product, stock, and vendor information.

```sql
CREATE TABLE inventory (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    stock INTEGER NOT NULL,
    cp REAL NOT NULL,
    sp REAL NOT NULL,
    totalcp REAL NOT NULL,
    totalsp REAL NOT NULL,
    assumed_profit REAL NOT NULL,
    vendor TEXT,
    vendor_phoneno TEXT
);
