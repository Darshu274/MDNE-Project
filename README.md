# MongoDB CRUD and Aggregation Project

This project demonstrates core MongoDB operations using Python and the `pymongo` library. It covers basic CRUD functionality, complex aggregation pipelines, and the implementation of multi-document transactions to ensure data atomicity in an e-commerce context.

---

## Project Structure

The project is organized into two primary folders containing Jupyter notebooks:

```
project-root/
│
├── task/               # Assignment notebooks with predefined tasks and requirements
│   ├── mongodb_training-checkpoints.ipynb  
│   └── orders-checkpoint.json     # Sample dataset for database initialization      
└── solution/           # Completed notebooks with Python implementations
    ├── mongodb_training.ipynb
    └── orders.json     
```

---

## Key Features

### 1. Database Management

- **Connection Establishment:** Uses `MongoClient` to connect to a local MongoDB server (typically `localhost:27017`).
- **Schema Design:** Manages a database named `shopDB` with collections for `users`, `products`, `orders`, and `reviews`.
- **Data Population:** Includes a structured dataset (`orders.json`) to initialize the database with German user records, various product categories (electronics, kitchen, books), and historical order data.

### 2. Multi-Document Transactions

To ensure data consistency, the project implements an atomic order creation process using MongoDB sessions. The `create_order_atomic` function coordinates several dependent operations:

- **User Handling:** Checks for existing users by email and creates new records if necessary.
- **Product Snapshots:** Captures product details (like name and price) at the time of purchase and embeds them directly into the order document.
- **Stock Validation:** Verifies sufficient inventory before allowing an order to proceed, aborting the transaction if stock is insufficient to prevent overselling.

### 3. Aggregation Pipelines

The project utilizes advanced aggregation stages to perform data analysis, such as:

- Calculating average, minimum, and maximum order values.
- Identifying high-spending users (e.g., those who ordered more than twice the average order value).
- Counting and sorting orders per user to identify top customers.

---

## Prerequisites

- **MongoDB Server:** Installed and running on your machine.
- **Python Libraries:**

```bash
pip install pymongo
```

---

## Usage

1. Start your local MongoDB instance.
2. Navigate to the `/solution` folder and open the `.ipynb` files in a Jupyter environment.
3. Ensure `orders.json` is in the project root to properly load the sample dataset.
4. Run the notebook cells to see CRUD operations, transaction handling, and aggregation results in action.
