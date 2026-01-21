# Cafe Sales Data Cleaning Project (Apple Numbers)

## Overview
This project showcases end-to-end data cleaning in Apple Numbers using a messy cafe sales dataset. The goal was to transform inconsistent and error-prone raw data into a clean, analysis-ready dataset while preserving transparency and traceability throughout the cleaning process.

## Dataset Description
The dataset contains cafe transaction records with the following fields:
- Item
- Quantity
- Price Per Unit
- Total Spent
- Payment Method
- Location
- Transaction Date

The raw data intentionally includes common real-world issues such as missing values, text stored as numbers, inconsistent capitalization, and invalid entries.

## Data Quality Issues Identified
- Blank and inconsistent item names
- Quantity and price stored as text
- Invalid values such as "Error" and "Unknown"
- Incorrect or misleading Total Spent values
- Inconsistent capitalization in text fields
- Missing or invalid transaction dates

## Cleaning Approach
To ensure accuracy and transparency, the following approach was used:
- Preserved all original (raw) columns and did not overwrite source data
- Created cleaned and final columns using formulas
- Standardized text fields by trimming extra spaces and converting text to uppercase
- Converted numeric text fields into usable numeric values
- Explicitly marked missing or invalid numeric values as "UNKNOWN"
- Recalculated Total Spent only when both Quantity and Price were valid
- Hid raw columns in the cleaned file to present a clean, analysis-ready view

This mirrors real-world analytics workflows where raw data is retained for traceability while cleaned data is used for reporting and analysis.

## Key Formulas Used

### Quantity_Cleaned_Final
```text
=IF(TRIM(F2)="","UNKNOWN",
   IF(ISNUMBER(VALUE(TRIM(F2))), VALUE(TRIM(F2)), "UNKNOWN"))
```

### Price_Per_Unit_Final
```text
=IF(TRIM(J2)="","UNKNOWN",
   IF(ISNUMBER(VALUE(TRIM(J2))), VALUE(TRIM(J2)), "UNKNOWN"))
```

### Total_Spent_Final
```text
=IF(OR(I2="UNKNOWN", L2="UNKNOWN"), "UNKNOWN", I2 * L2)
```

### Text Standardization (Item, Location, Payment Method)
```text
=IF(TRIM(A2)="","UNKNOWN", UPPER(TRIM(A2)))
```

## Before & After Examples
Screenshots below show original and cleaned columns side-by-side to highlight key cleaning steps.

![Item Cleaning](screenshots/01_item_cleaning.png)
![Quantity Cleaning](screenshots/02_quantity_cleaning.png)
![Price Cleaning](screenshots/03_price_cleaning.png)
![Total Spent](screenshots/04_total_spent.png)
![Location & Payment Method](screenshots/05_location_payment.png)
![Transaction Date](screenshots/06_transaction_date.png)

## Files in This Repository
```
/data
  Cafe_Sales_Raw.numbers
  Cafe_Sales_Cleaned.numbers
/screenshots
  01_item_cleaning.png
  02_quantity_cleaning.png
  03_price_cleaning.png
  04_total_spent.png
  05_location_payment.png
  06_transaction_date.png
README.md
```

## Outcome
The final dataset is clean, consistent, and safe for analysis. All transformations are formula-based, clearly documented, and reproducible. This project demonstrates practical spreadsheet data cleaning skills and best practices for maintaining data integrity.

## Next Steps
The cleaned dataset can now be used for:
- Sales analysis and reporting
- Data visualization and dashboards
- Migration to SQL, Python, or BI tools
