
# Coffee Sales Project

## Overview
This project involves analyzing coffee sales using three distinct tables:

1. **Order Table** with columns:
   - Order ID
   - Order Date
   - Customer ID
   - Product ID
   - Quantity

2. **Customer Table** with columns:
   - Customer ID
   - Customer Name
   - Email
   - Phone Number
   - Address
   - City
   - Country
   - Post Code
   - Loyalty Card

3. **Product Table** with columns:
   - Product ID
   - Coffee Type
   - Roast Type
   - Size
   - Unit Price
   - Price per 100kg
   - Profit

## Project Tasks
1. **Total Sales Over Time:**
   - Created a pivot table with Order Date in rows and Sales in values.
   - Used a line chart to visualize total sales over time.
  
2. **Top 4 Cities with Highest Sales:**
   - Created a pivot table with City in rows and Sales in values.
   - Used a bar chart to visualize the top 4 cities with the highest sales.
  
3. **Country with the Highest Sales:**
   - Created a pivot table with Country in rows and Sales in values.
   - Used a bar chart to visualize sales by country.
  
4. **Top 5 Customers Who Purchase Coffee:**
   - Created a pivot table with Customer Name in rows and Sales in values.
   - Used a bar chart to visualize the top 5 customers.
  
5. **Top 5 Coffee Type Sales in Different Countries:**
   - Created a pivot table with Coffee Type in rows, Country in columns, and Sales in values.
   - Used a bar chart to visualize coffee type sales by country.

## Data Cleaning Process
To effectively analyze the data, new columns were created in the Order table, derived from the Customer and Product tables:

- **New Columns in the Order Table:**
  - Customer Name
  - Email
  - Country
  - Coffee Type
  - Roast Type
  - Size
  - Unit Price
  - Sales
  - Coffee Type Name
  - Roast Type Name
  - Loyalty Card

## Data Gathering
To populate these new columns, formulas such as XLOOKUP and INDEX were used.

- **Populating Customer Data:**
  - **Customer Name:**
    ```excel
    =XLOOKUP(C2, customers!$A$1:$A$1001, customers!$B$1:$B$1001, , 0)
    ```
    This formula retrieves the Customer Name from the Customer table into the Order table.
  - **Email, Country, and Loyalty Card:**
    The same XLOOKUP approach was used, adjusting the referenced columns accordingly.

- **Handling Blank Cells:**
  If blank cells in the Email column return "0", the following IF formula can be used to return a blank instead:
  ```excel
  =IF(XLOOKUP(C2, customers!$A$1:$A$1001, customers!$C$1:$C$1001, , 0) = 0, "", XLOOKUP(C2, customers!$A$1:$A$1001, customers!$C$1:$C$1001, , 0))
  ```

- **Populating Product Data:**
  The INDEX formula was used to populate multiple columns dynamically:
  ```excel
  =INDEX(products!$A$1:$G$49, MATCH(orders!$D2, products!$A$1:$A$49, 0), MATCH(orders!I$1, products!$A$1:$G$1, 0))
  ```
  This formula populates Coffee Type, Roast Type, Size, and Unit Price columns.

- **Sales Calculation:**
  The Sales column was calculated using:
  ```excel
  =L2 * E2
  ```

## Data Formatting
- **Order Date:**
  Formatted to "dd-mmm-yyyy" using custom format.
- **Size:**
  Formatted to "0.0 Kg" for consistency.
- **Unit Price and Sales:**
  Formatted with the dollar currency sign.

## Data Consistency
- **Abbreviations:**
  Created new columns for full Coffee Type and Roast Type names using IF formulas:
  - Coffee Type Name:
    ```excel
    =IF(I2="Rob", "Robusta", IF(I2="Exc", "Excelsa", IF(I2="Ara", "Arabica", IF(I2="Lib", "Liberica", ""))))
    ```
  - Roast Type Name:
    ```excel
    =IF(J2="M", "Medium", IF(J2="L", "Light", IF(J2="D", "Dark", "")))
    ```

## Checking for Duplicates
Used Excel's "Remove Duplicates" feature to ensure data integrity.

## Converting Data to Table
Converted the data to a table using `Ctrl + T` and named it "ORDERS".

## Data Visualization

### Detailed Steps for Data Visualization

- **Creating Pivot Tables and Charts:**
  - **Total Sales Over Time:**
    - Dragged Order Date into rows, Coffee Type Name into columns, and Sales into values.
    - Used a line chart for visualization.
  
  - **Country Bar Chart:**
    - Added Sales to values and Country to rows.
    - Formatted as a bar chart to compare sales across countries.
  
  - **Top 5 Customers, Sales by Country, Coffee Type Sales by Country:**
    - Used bar charts for clear comparison.
  
  - **Top 4 Cities Sales:**
    - Used a pie chart to highlight proportions and relationships.

- **Dashboard Creation:**
  - Moved all charts to a new sheet named "Dashboard".
  - Linked slicers for interactive filtering.
  - Removed gridlines for a clean presentation.

These steps provided a comprehensive analysis of coffee sales, ensuring data accuracy and effective visualization for insights.
```