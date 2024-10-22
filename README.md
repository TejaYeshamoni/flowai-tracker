# Personal Expense Tracker API

This is a **RESTful API** for managing personal financial records. Users can record their income and expenses, retrieve past transactions, and get summaries by category or time period. It is built using **Node.js** with **Express.js** and **SQLite**.

## Table of Contents
1. [Features](#features)
2. [Technologies Used](#technologies-used)
3. [Requirements](#requirements)
4. [Installation](#installation)
5. [Running the Project Locally](#running-the-project-locally)
6. [API Endpoints](#api-endpoints)
7. [Database Structure](#database-structure)
8. [Deployment](#deployment)
9. [Contributing](#contributing)
    
---

## Features

- Add income and expenses with different categories.
- Retrieve all transactions or specific ones by ID.
- Update and delete transactions.
- View a summary of income, expenses, and balance.
- Optional filtering of summary by date range or category.

---

## Technologies Used

- **Node.js**: Backend runtime environment
- **Express.js**: Web framework for Node.js
- **SQLite**: Lightweight database for storing transactions
- **Render**: For deployment

---

## Requirements

- **Node.js** (v14 or later)
- **npm** (comes with Node.js)
- **SQLite3** (optional, the project sets it up automatically)

---

## Installation

1. Clone the repository to your local machine:
   ```bash
   git clone https://github.com/TejaYeshamoni/flowai-tracker.git
   ```

2. Navigate to the project directory:
   ```bash
   cd personal-expense-tracker
   ```

3. Install the dependencies:
   ```bash
   npm install
   ```

4. Make sure SQLite database is set up in the `database` folder.

---

## Running the Project Locally

1. Start the server:
   ```bash
   node app.js
   ```

2. The API will be available at:
   ```
   http://localhost:3000
   ```

### Test the API using Postman or cURL

---

## API Endpoints

Here are the available API endpoints:

### **POST** /api/transactions
Add a new transaction.

- **Request Body (JSON)**:
  ```json
  {
    "type": "income",
    "category": "Salary",
    "amount": 5000,
    "date": "2024-10-22",
    "description": "October Salary"
  }
  ```

- **Response**:
  ```json
  {
    "id": 1
  }
  ```

---

### **GET** /api/transactions
Retrieve all transactions.

- **Response**:
  ```json
  [
    {
      "id": 1,
      "type": "income",
      "category": "Salary",
      "amount": 5000,
      "date": "2024-10-22",
      "description": "October Salary"
    }
  ]
  ```

---

### **GET** /api/transactions/:id
Retrieve a specific transaction by ID.

- **Response**:
  ```json
  {
    "id": 1,
    "type": "income",
    "category": "Salary",
    "amount": 5000,
    "date": "2024-10-22",
    "description": "October Salary"
  }
  ```

---

### **PUT** /api/transactions/:id
Update a transaction by ID.

- **Request Body (JSON)**:
  ```json
  {
    "type": "expense",
    "category": "Groceries",
    "amount": 300,
    "date": "2024-10-23",
    "description": "Grocery shopping"
  }
  ```

- **Response**:
  ```json
  {
    "message": "Transaction updated successfully"
  }
  ```

---

### **DELETE** /api/transactions/:id
Delete a transaction by ID.

- **Response**:
  ```json
  {
    "message": "Transaction deleted successfully"
  }
  ```

---

### **GET** /api/summary
Retrieve a summary of transactions (total income, expenses, balance). Can be filtered by category or date range.

- **Example Response**:
  ```json
  {
    "total_income": 5000,
    "total_expenses": 300,
    "balance": 4700
  }
  ```

---

## Database Structure

### `transactions` Table:
| Column     | Type    | Description                   |
|------------|---------|-------------------------------|
| id         | INTEGER | Primary key (autoincrement)    |
| type       | TEXT    | Transaction type (income/expense) |
| category   | TEXT    | Category of transaction        |
| amount     | REAL    | Amount of transaction          |
| date       | TEXT    | Date of transaction            |
| description| TEXT    | Additional details             |

### `categories` Table (Optional):
| Column     | Type    | Description                   |
|------------|---------|-------------------------------|
| id         | INTEGER | Primary key (autoincrement)    |
| name       | TEXT    | Category name                 |
| type       | TEXT    | Category type (income/expense)|

---

## Deployment

### Deploying on Render

Follow these steps to deploy on **Render**:

1. **Push your code to GitHub**:
   ```bash
   git push origin master
   ```

2. **Create a new Web Service** on Render:
   - Go to [Render](https://render.com) and create an account.
   - Click **New Web Service** and link your GitHub repository.
   - Set the environment to **Node.js**.
   - In your repository settings, make sure the `start` script in your `package.json` is set to:
     ```json
     "scripts": {
       "start": "node app.js"
     }
     ```

3. **Start the Deployment**:
   - Click **Create Web Service** and Render will handle the deployment.
   - Once deployed, you’ll get a live URL for your app (e.g., `https://your-app-name.onrender.com`).

4. **Test the deployed API**:
   Use Postman or cURL with the Render URL to test the API endpoints.

---

## Contributing

1. Fork the repository.
2. Create a new feature branch:
   ```bash
   git checkout -b feature-branch
   ```
3. Commit your changes:
   ```bash
   git commit -m "Add a new feature"
   ```
4. Push to the branch:
   ```bash
   git push origin feature-branch
   ```
5. Open a pull request.
