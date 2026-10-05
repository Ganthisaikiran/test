# Zepto Product Inventory Analysis

A PostgreSQL data analysis project exploring product pricing, discounts, stock availability, product weights, and category-level inventory metrics for a Zepto-style quick-commerce catalog.

## Project Overview

This project demonstrates a practical SQL workflow:

- Creating a structured PostgreSQL table for product inventory data
- Checking row counts, sample records, null values, duplicate product names, and stock status
- Cleaning prices stored in paise and converting them to rupees
- Comparing discounts, prices, product weights, and stock availability
- Aggregating estimated inventory value and inventory weight by category

This repository is an adaptation of the original project by [Amlan Mohanty](https://github.com/amlanmohanty1/zepto-SQL-data-analysis-project). The SQL workflow and dataset structure are based on that project and its accompanying tutorial. Any changes or additional analysis in this repository should be clearly identified as my own work.

## Files

| File | Description |
| --- | --- |
| `Zepto_SQL_data_analysis.sql` | PostgreSQL table definition, data-quality checks, cleaning queries, and analysis queries |
| `zepto_v2.csv` | Product catalog dataset used by the analysis |

## Tools Used

- PostgreSQL
- SQL
- CSV data

## Analysis Questions

The script answers questions such as:

1. Which products have the highest discount percentages?
2. Which high-MRP products are out of stock?
3. What is the estimated inventory value by category?
4. Which products have an MRP above 500 and a discount below 10%?
5. Which categories have the highest average discount?
6. Which products offer the lowest price per gram?
7. How can products be grouped by weight as Low, Medium, or Bulk?
8. What is the total inventory weight by category?

## Setup and Usage

### 1. Create the table

Open a PostgreSQL client such as `psql` or pgAdmin and run the table creation section in `Zepto_SQL_data_analysis.sql`.

### 2. Load the CSV

After creating the table, load the CSV file using PostgreSQL's `COPY` command. Update the path for your computer:

```sql
\copy zepto(category, name, mrp, discountPercent, availableQuantity, discountedSellingPrice, weightInGms, outOfStock, quantity)
FROM 'C:/path/to/zepto_v2.csv'
WITH (FORMAT csv, HEADER true, QUOTE '"');
```

The `\copy` command is a `psql` command. In pgAdmin, use its Import/Export Data feature with the first row treated as column headers.

### 3. Run the analysis

Run the remaining statements in `Zepto_SQL_data_analysis.sql` in order. The cleaning section removes zero-MRP records and converts the two price columns from paise to rupees before the analysis queries run.

## Data Notes and Limitations

- The dataset contains 3,732 product records at the time of analysis.
- Prices appear to be stored in paise before conversion to rupees.
- `availableQuantity` is used as the inventory quantity in category-level calculations.
- The query labelled estimated revenue is an estimated inventory value, not confirmed sales revenue, because the dataset does not contain transaction or order history.
- Product names can appear under multiple SKUs, so duplicate names do not necessarily represent duplicate records.
- The dataset source and license must be added below before publishing this repository.


## Attribution and Licensing

- **Original project:** [Amlan Mohanty's Zepto SQL Data Analysis Project](https://github.com/amlanmohanty1/zepto-SQL-data-analysis-project)
- **Tutorial:** [SQL Data Analyst Portfolio Project using Zepto Inventory Dataset](https://www.youtube.com/watch?v=x8dfQkKTyP0)
- **Dataset:** [Zepto Inventory Dataset on Kaggle](https://www.kaggle.com/datasets/palvinder2006/zepto-inventory-dataset)
- **Dataset context:** The source repository states that the data was scraped from Zepto product listings. This repository does not claim ownership of that data.
- **Source repository license:** The original repository includes an MIT license. Verify that the license terms also cover the dataset before redistributing the CSV.

This repository is intended for learning and portfolio demonstration. Keep the attribution above when publishing an adapted version.

## Résumé Description

## Résumé Description

> Built a PostgreSQL inventory analysis project for a Zepto-style product catalog, performing data-quality checks, price normalization, discount analysis, stock segmentation, price-per-gram comparisons, and category-level inventory aggregation.

Use wording such as: “Adapted and extended a PostgreSQL inventory analysis project based on a public Zepto dataset, performing data-quality checks, price normalization, discount analysis, stock segmentation, price-per-gram comparisons, and category-level inventory aggregation.”
