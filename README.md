# Online Retail Inventory Analytics and Inventory Optimization

## Project Overview

This project applies inventory analytics and operations management techniques to the Online Retail dataset. The objective is to transform raw transaction data into actionable inventory decisions by combining data cleaning, demand analysis, inventory optimization, and risk simulation.

The project follows a complete analytics workflow:

```text
Raw Transaction Data
        ↓
Data Cleaning
        ↓
Revenue Analysis
        ↓
ABC Inventory Classification
        ↓
Demand Analysis
        ↓
Newsvendor Optimization
        ↓
Monte Carlo Simulation
```

By integrating historical sales analysis with inventory decision models, this project demonstrates how data-driven methods can support inventory planning under demand uncertainty.

---

## Business Problem

Inventory managers must balance two competing risks:

- Ordering too much inventory, resulting in excess stock and unnecessary holding costs.
- Ordering too little inventory, resulting in stockouts and missed sales opportunities.

The challenge is determining an appropriate order quantity when future demand is uncertain.

This project investigates how different cost assumptions influence inventory decisions and evaluates the resulting risks using simulation.

---

## Dataset

### Online Retail Dataset

The dataset contains transactional records from a UK-based online retailer, including:

- InvoiceNo
- StockCode
- Description
- Quantity
- InvoiceDate
- UnitPrice
- CustomerID
- Country

---

## Repository Structure

```text
├── notebooks/
│   ├── 1_data_cleaning_ABC_analysis.ipynb
│   ├── 2_demand_modelling.ipynb
│   ├── 3_newsvendor_model.ipynb
│   └── 4_monte_carlo_simulation.ipynb
│
├── README.md
│
└── data/
    └── (not included in repository)
```

Notebooks should be executed sequentially from Notebook 1 to Notebook 4.

---

## Data Availability

Data files are not included in this repository due to file size limitations.

The original dataset can be downloaded from Kaggle:

**Online Retail Dataset:**  
https://www.kaggle.com/datasets/carrie1/ecommerce-data

All intermediate datasets used throughout the project can be reproduced by running the notebooks in sequence.

---

## Project Structure

### 1. Data Cleaning and Preprocessing

The raw dataset required extensive preprocessing before analysis.

#### Cleaning Tasks

- Handling missing values
- Removing duplicate transactions
- Identifying and removing cancelled orders
- Removing invalid quantity and pricing records
- Filtering non-inventory stock codes
- Converting date fields into datetime format

#### Output

A clean transaction dataset suitable for inventory analysis and demand modelling.

### 2. Revenue Analysis

Revenue was calculated as:

```text
Revenue = Quantity × UnitPrice
```

The analysis was used to:

- Identify high-value products
- Measure product-level revenue contribution
- Understand sales concentration within the business

### 3. ABC Inventory Analysis

Products were classified according to their contribution to total revenue using Pareto analysis.

#### Results

| Class | Revenue Contribution |
|---------|---------|
| A | ~80% |
| B | ~15% |
| C | ~5% |

Additional findings:

- Class A contained 784 SKUs.
- 231 high-priority SKUs were selected for further demand analysis.

#### Business Insight

ABC analysis helps prioritize inventory management resources by focusing attention on the products that contribute the most revenue.
