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

`HR Dashboard sample`
![hr dashboard sample](https://github.com/user-attachments/assets/e286bc6c-d663-4013-8090-92e500897258)


## DAX & Power Query Code Samples

### Assigning Undisclosed Gender
```powerquery
= Table.ReplaceValue(#"Change Type","","Undisclosed",Replacer.ReplaceValue,{"Gender"})
```

### Creating Dept Rating (Power Query Custom Column)
```powerquery
= Table.AddColumn(#"Unpivoted Columns", "Dept Rating", each [Department]&"/"&[Attribute])
```

### Calculating Annual Bonus (DAX)
```DAX
= Table.AddColumn(#"Replaced Value", "Annual Bonus", each [Salary]*[Bonus Rate])
```

### Calculating Total Pay (DAX)
```DAX
= Table.AddColumn(#"Added Custom", "Total Pay", each [Salary]+[Annual Bonus])
```

### Salary Band (Power Query Conditional Column)
``` power query
if [Salary] <= 30000 then "$20,000 - $30,000" else if [Salary] <= 40000 then "$30,000 - $40,000" else if [Salary] <= 50000 then "$40,000 - $50,000" else if [Salary] <= 60000 then "$50,000 - $60,000" else if [Salary] <= 70000 then "$60,000 - $70,000" else if [Salary] <= 80000 then "$70,000 - $80,000" else if [Salary] <= 90000 then "$80,000 - $90,000" else if [Salary] <= 100000 then "$90,000 - $100,000" else if [Salary] <= 110000 then "$100,000 - $110,000" else if [Salary] <= 120000 then "$110,000 - $120,000" else "Above $120,000")
```

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
- `Hr dashboard sample` - jpg. snapshot of dashboard showing important data and insights.

## How to Explore

1. Open `Ejigha_Godswill_Palmoria_GROUP_ANALYSIS.pbix` in Power BI Desktop
2. Review each report page & dashboard visuals
3. Use slicers (Region, Department) to filter and explore

## Author

**Ejigha Godswill**  
HR & Data Analytics Consultant  
Email: [Godswillejigha6@gmail.com]  
Portfolio: [[Ejigha Godswill Portfolio](https://github.com/prideofimo)]
