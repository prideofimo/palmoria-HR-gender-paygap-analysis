# palmoria HR gender paygap analysis
This is where I started my portfolio building and DSA project. HR analytics case study of Palmoria Group using Power BI — uncovering gender distribution, pay gap, and salary compliance issues, with actionable insights and dashboards
# Palmoria Group HR Gender & Pay Gap Analysis

## Overview

This project was developed as part of an HR analytics case study for Palmoria Group, a Nigerian manufacturing company. The company faced scrutiny over alleged gender inequality and pay disparities, which threatened its reputation and growth ambitions.

The goal of this analysis was to investigate gender-related issues in the workforce, salary structure compliance, and bonus allocation, and provide actionable insights to management.

It also represents a milestone in my portfolio-building journey and showcases practical skills in Power BI data modeling, cleaning, DAX, and dashboard design.

## Dataset

Two HR datasets were provided:
- **Palmoria Employee Data:** containing employee demographics, salary, region, department, and performance ratings.
- **Bonus Mapping Data:** defining rules for bonus allocation based on department and rating.

These were imported into Power BI, cleaned, modeled, and visualized.

## Data Cleaning & Preparation

Steps performed:
- Used first row as header
- Renamed columns (e.g., `Location` → `Region`)
- Removed rows with `NULL` in department
- Removed employees without salary (they were no longer with the company)
- Assigned `"Undisclosed"` to employees who did not specify their gender
- Changed column data types appropriately (salary to numeric, regions to text, etc.)
- Created calculated and conditional columns:
  - `Dept Rating` → to map department & rating to bonus table
  - `Annual Bonus` → salary × bonus rate
  - `Total Pay` → salary + annual bonus
  - `Salary Band` → salary grouped in $10,000 bands (e.g., $10,000–$20,000, >$120,000)

## Key Business Questions Answered

- What is the gender distribution across the company, by region and by department?
- How do employee ratings vary by gender?
- Is there evidence of a gender pay gap? If so, in which departments and regions?
- Does Palmoria comply with the minimum salary regulation of $90,000?
- How are employees distributed across salary bands company-wide and by region?
- What is the total annual bonus allocation by employee, by region, and company-wide?
- What is the total pay (salary + bonus) by employee, by region, and company-wide?

## Dashboard

An interactive Power BI dashboard was created with:
- Gender distribution visuals (company-wide, by region, by department)
- Ratings by gender
- Salary structure and pay gap visuals
- Salary band distributions
- Compliance KPIs (e.g., minimum salary compliance rate)
- Bonus allocation summaries
- Slicers for filtering by Region and Department

## DAX & Power Query Code Samples

### Assigning Undisclosed Gender
```powerquery
= Table.ReplaceValue(#"PreviousStep", null, "Undisclosed", Replacer.ReplaceValue, {"Gender"})
```

### Creating Dept Rating (Power Query Custom Column)
```powerquery
= [Department] & " - " & Text.From([Rating])
```

### Calculating Annual Bonus (DAX)
```DAX
Annual Bonus = 'Employee Data'[Salary] * RELATED('Bonus Mapping'[Bonus Rate])
```

### Calculating Total Pay (DAX)
```DAX
Total Pay = 'Employee Data'[Salary] + 'Employee Data'[Annual Bonus]
```

### Salary Band (Power Query Conditional Column)

| Condition           | Output            |
|----------------------|-------------------|
| Salary <= 20000     | `$10,000–$20,000` |
| Salary <= 30000     | `$20,000–$30,000` |
| …                   | …                 |
| Salary > 120000     | `>$120,000`       |

## Key Insights

- Gender imbalance observed in certain departments and regions
- Evidence of gender pay disparities in specific regions & departments
- Many employees do not meet the $90,000 minimum salary requirement — especially in certain regions/departments
- Bonus allocation skews slightly toward higher-rated male employees
- Salary distribution clusters heavily between $70,000–$90,000 bands

## Tools & Techniques

- Power BI Desktop
- Power Query for data cleaning & transformations
- Data modeling (relationships between employee & bonus mapping tables)
- DAX for calculated columns & KPIs
- Dashboard & report design (slicers, cards, charts)

## Repository Contents

- `Ejigha_Godswill_Palmoria_GROUP_ANALYSIS.pbix` — Power BI file with all data, model, and dashboard

## How to Explore

1. Open `Ejigha_Godswill_Palmoria_GROUP_ANALYSIS.pbix` in Power BI Desktop
2. Review each report page & dashboard visuals
3. Use slicers (Region, Department) to filter and explore

## Author

**Ejigha Godswill**  
HR & Data Analytics Consultant  
Email: [Godswillejigha6@gmail.com]  
Portfolio: [your portfolio link]
