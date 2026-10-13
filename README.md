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

## 4. Demand Analysis

A representative SKU from the high-value product group was selected for demand analysis.

### Method

- Aggregate transactions into weekly demand
- Examine demand distribution
- Analyze time-series patterns
- Calculate descriptive statistics

### Demand Statistics

```text
Mean Weekly Demand ≈ 233 units
Standard Deviation ≈ 109 units
```

### Business Insight

The selected SKU exhibits substantial demand variability, making inventory planning under uncertainty an important challenge.

---

## 5. Newsvendor Model

The Newsvendor model was used to determine optimal inventory levels under different business assumptions.

The critical ratio was calculated as:

```text
Critical Ratio = Cu / (Cu + Co)
```

where:

- Cu = Underage Cost
- Co = Overage Cost

The optimal order quantity was determined using a normal demand assumption.

### Assumption Disclaimer

Since the dataset does not contain product selling prices, purchase costs, or salvage values, the following scenarios were created as illustrative business cases to demonstrate how different cost structures affect inventory decisions.

---

### Scenario 1: Balanced Costs

#### Assumptions

```text
Selling Price = 10
Purchase Cost = 6
Salvage Value = 2
```

#### Result

```text
Optimal Order Quantity = 233 units
```

#### Interpretation

The costs of understocking and overstocking are balanced, resulting in an order quantity close to average demand.

---

### Scenario 2: Stockouts are Expensive

#### Assumptions

```text
Selling Price = 15
Purchase Cost = 6
Salvage Value = 2
```

#### Result

```text
Optimal Order Quantity = 288 units
```

#### Interpretation

The higher cost of missed sales encourages a more aggressive inventory policy and a larger order quantity.

---

### Scenario 3: Excess Inventory is Costly

#### Assumptions

```text
Selling Price = 10
Purchase Cost = 7
Salvage Value = 1
```

#### Result

```text
Optimal Order Quantity = 187 units
```

#### Interpretation

The higher cost of excess inventory encourages a more conservative inventory policy and a smaller order quantity.

---

### Monte Carlo Simulation

A Monte Carlo simulation was conducted to evaluate inventory performance under demand uncertainty.

#### Method

- Generate 1,000 random demand scenarios based on historical demand data
- Evaluate inventory performance using Newsvendor order quantities
- Calculate resulting profits under each scenario
- Compare inventory policies across different cost assumptions

A fixed random seed was used to ensure reproducibility.

#### Simulation Results

| Scenario | Optimal Q | Average Profit |
|-----------|-----------|---------------|
| Balanced Costs | 233 | 604 |
| Stockouts Expensive | 288 | 1643 |
| Excess Inventory Costly | 187 | 245 |

---

### Key Findings

#### Balanced Costs

- Produced a balanced inventory strategy
- Generated moderate expected profit
- Balanced stockout and inventory risks

#### Stockouts Expensive

- Generated the largest order quantity
- Produced the highest expected profit
- Increased inventory exposure

#### Excess Inventory Costly

- Generated the smallest order quantity
- Reduced inventory exposure
- Increased stockout risk
- Produced the lowest expected profit

---

### Business Insights

This project demonstrates that inventory decisions should not rely solely on average demand.

Effective inventory management requires balancing:

- Demand uncertainty
- Stockout costs
- Excess inventory costs
- Profitability considerations
- Inventory risk

#### Key Observations

- Higher order quantities increase potential sales and profit.
- Higher order quantities also increase inventory risk.
- Lower order quantities reduce inventory exposure but increase stockout risk.
- Even optimal inventory policies cannot eliminate uncertainty.

---

### Technical Skills Demonstrated

#### Data Analytics

- Data Cleaning
- Exploratory Data Analysis (EDA)
- Revenue Analysis
- Demand Analysis
- Inventory Analytics

#### Inventory Management

- ABC Classification
- Newsvendor Model
- Inventory Optimization
- Cost Trade-off Analysis

#### Simulation and Decision Analysis

- Monte Carlo Simulation
- Risk Evaluation
- Scenario Analysis
- Decision-Making Under Uncertainty

#### Tools

- Python
- Pandas
- NumPy
- SciPy
- Matplotlib
- Seaborn
- Jupyter Notebook

---

## References

### Dataset

**Online Retail Dataset**  
https://www.kaggle.com/datasets/carrie1/ecommerce-data

### Reference Project

**E-Commerce Customer Purchase Analysis**  
https://github.com/idealidler/E-Commerce-Customer-Purchase-Analysis

Used as an initial reference for:

- Data cleaning workflow
- Exploratory data analysis (EDA)
- Transaction preprocessing techniques

### Inventory Modeling

**Newsvendor Model**  
https://github.com/takazawa/newsvendor-model

Referenced for:

- Newsvendor problem formulation
- Critical ratio calculation
- Inventory optimization concepts

### Monte Carlo Simulation

**Python Monte Carlo Simulation Tutorial: The Newsvendor Problem (Beginner Friendly)**  
https://www.youtube.com/watch?v=49xGXQoIV00

Referenced for:

- Monte Carlo simulation workflow
- Demand scenario generation
- Inventory performance evaluation

---

## Disclaimer

This project is an independent educational implementation developed using the above resources for learning purposes.

The data cleaning process, ABC inventory analysis, SKU selection, demand aggregation, Newsvendor implementation, Monte Carlo simulation, business interpretations, and project structure were adapted and extended to investigate inventory decision-making under demand uncertainty.

---

## Conclusion

This project developed a complete inventory analytics workflow using real-world retail transaction data.

Beginning with raw transaction records, the analysis progressed through data cleaning, revenue analysis, ABC inventory classification, demand modelling, Newsvendor optimization, and Monte Carlo simulation.

The results demonstrate how cost assumptions influence inventory decisions and highlight the trade-off between inventory availability and inventory risk. Overall, the project illustrates how analytical models can support inventory management decisions under uncertain demand conditions.
