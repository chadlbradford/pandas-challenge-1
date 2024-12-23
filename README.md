# README: Pandas-Challenge-1

## **Summary**
This was an interesting first foray into using the pandas library in python.  The main discovery was recognizing there are many ways to complete the defined tasks.  The most difficult aspect was maintaining control of the numerous dataframes and lists created throughout the process.  I also recognized potential improvements by re-utilizing defined lists in downstream code.  

## **Overview**

This script analyzes a client dataset to extract insights into client behavior, product sales, and profitability. It uses **Pandas** for data analysis and processes the dataset through four main steps:
1. **Exploring the data**.
2. **Transforming raw data into meaningful metrics**.
3. **Validating calculations with known data**.
4. **Summarizing and analyzing results**.

---

## **Dataset**

The dataset includes **54,639 entries** and **24 columns**, providing detailed information about:
- **Client Information**: Name, contact details, job title, etc.
- **Order Details**: Order ID, date, year, and week.
- **Product Information**: Category, subcategory, unit price, cost, weight, and quantity.
- **Derived Metrics**: Line subtotals, shipping prices, total prices, costs, and profits.

---

## **Script Workflow**

### **Part 1: Explore the Data**
1. **Load the dataset**: Read the CSV file into a Pandas DataFrame.
2. **Data exploration**:
   - View column names, data types, and statistics (`.describe()`).
   - Identify the three most common product categories.
   - Determine the most frequent subcategory within the top category.
   - Identify the five clients with the most entries and their total units ordered.

### **Part 2: Transform the Data**
1. Add derived columns for analysis:
   - **Line Subtotal**: `unit_price * qty`.
   - **Total Weight**: `unit_weight * qty`.
   - **Shipping Price**: Based on weight (\$7/lb if >50 lbs, otherwise \$10/lb).
   - **Line Price**: `line_subtotal + shipping_price` with a sales tax of 9.25%.
   - **Line Cost**: `unit_cost * qty + shipping_price`.
   - **Line Profit**: `line_price - line_cost`.

2. Display intermediate calculations for verification.

### **Part 3: Confirm Your Work**
- Validate the `line_price` calculations for specific orders:
  - Match totals for **Order IDs 2742071, 2173913, and 6128929** against known receipts.

### **Part 4: Summarize and Analyze**
1. Identify the top 5 clients (from Part 1) and their total spending.
2. Create a summary DataFrame for the top 5 clients:
   - **Total Units Purchased**.
   - **Total Shipping Price**.
   - **Total Revenue**.
   - **Total Profit**.
3. Convert monetary columns to millions for readability.
4. Sort the summary by **Total Profit (millions)** in descending order.
5. Display and export the final sorted summary.

---

## **Key Outputs**

### **Top 3 Product Categories**
- Consumables: 23,538 entries.
- Furniture: 11,915 entries.
- Software: 8,400 entries.

### **Top 5 Clients by Entries**
| Client ID | Count |
|-----------|-------|
| 33615     | 220   |
| 66037     | 211   |
| 46820     | 209   |
| 38378     | 207   |
| 24741     | 207   |

### **Validation Results**
| Order ID  | Total Line Price |
|-----------|------------------|
| 2173913   | \$162,388.71     |
| 2742071   | \$152,811.89     |
| 6128929   | \$923,441.25     |

### **Top 5 Clients Summary**
| Client ID | Units  | Shipping (millions) | Total Revenue (millions) | Total Profit (millions) |
|-----------|--------|----------------------|--------------------------|--------------------------|
| 24741     | 239862 | 5.13                | 82.27                    | 36.58                   |
| 33615     | 64313  | 1.83                | 8.38                     | 2.20                    |
| 38378     | 73667  | 3.43                | 12.91                    | 3.27                    |
| 46820     | 75768  | 1.60                | 9.74                     | 2.74                    |
| 66037     | 43018  | 1.40                | 10.26                    | 3.26                    |

---

## **Dependencies**

- **Python 3.7+**
- **Pandas Library**

## **References**
Chatgpt was used to troubleshoot self generated code.
