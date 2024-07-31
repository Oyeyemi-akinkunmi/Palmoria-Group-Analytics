# Palmoria Group Analytics
## Table of Content
- [Project Overview](#project-overview)
- [Data Source](#data-source)
- [Tools](#tools)
- [Approach](#approach)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results](#results)
- [Recommendations](#recommendations)
- [Limitation](#limitation)

### Project Overview
This project seeks to conduct a comprehensive data analysis of the HR data of Palmoria Group. 
Palmoria Group (fictional) is a manufacturing embroiled in issues bordering on gender inequality in the three regions; Lagos, Abuja and Kaduna.
The analysis focuses on the gender distribution of employees across the regions, employee ratings and remuneration.

### Data Source
There are two CSV files, both primary data from Palmoria Group Human Resources database. 
One contains employee details, rating and salary. 
The second datasets contains the bonus rules for employees based on ratings and department.

### Tools
- Microsoft Excel
- PowerBI

### Approach
Some data wrangling processes include:
- Handling missing values
- Removing irrelevant data
- Using Excel functions (XLOOKUP, SUM, SUMIFS) to merge data from different sheets, and to create columns needed for analysis.

### Exploratory Data Analysis
1. Conducted comprehensive EDA using PowerBI to distill gender distribution in the organization into regions and departments
2. Examined employees ratings based on gender across the three different region of Palmoria Group operations.
3. Scrutinized the company’s salary structure to identify gender pay gap across regions and departments.
4. Investigated the company’s salary structure to ascertain compliance with regulation which requires manufacturing companies to pay employees a minimum of $90,000.
5. Categorized pay distribution of employees grouped by a band of $10,000.
6. Computed using functions and formulas in Excel, total amount to be paid to individual employees (salary inclusive of bonus)
7. Maximized power of DAX in PowerBI to compute the total amount to be paid out per region and company-wide.

### Data Analysis
- PowerBI DAX:

`Employees above $90k = CALCULATE(COUNT(Data[Salary]), Data[Net Salary] >=90000)
Employees Below $90k = CALCULATE(COUNT(Data[Salary]), Data[Net Salary] <90000)
Overall net Salary = SUM(Data[Net Salary])
Total Abuja Amount = CALCULATE(SUM(Data[Net Salary]),Data[Location]="Abuja")
Total Lagos Amount = CALCULATE(SUM(Data[Net Salary]),Data[Location]="Lagos")
Total Kaduna Amount = CALCULATE(SUM(Data[Net Salary]),Data[Location]="Kaduna")
Total Females = CALCULATE(COUNT(Data[Name]),Data[Gender]="Female")
Total Males = CALCULATE(COUNT(Data[Name]),Data[Gender]="Male")`

- MS Excel Formulas:
Formula to calculate bonus for each employee based on rating and department:
`=XLOOKUP(C2,'Bonus Rules'!$B$3:$B$14,XLOOKUP(F2,'Bonus Rules'!$C$2:$G$2,'Bonus Rules'!$C$3:$G$14," "))`

Formula to calculate  bonus:
`=[@[Bonus %]]*[@Salary]`

Formula to calculate total salary:
`=[@Bonus]+[@Salary]`

Formula to calculate salary band:
`=ROUNDDOWN([@Salary]/10000,0)*10000&" - "&ROUNDDOWN([@Salary]/10000,0)*10000+10000`

Formula to count employees by salary band:
`=COUNTIFS(Table1[Salary],"=>10000",Table1[Salary],"<=19999")
=COUNTIFS(Table1[Salary],">20000",Table1[Salary],"<=30000")
=COUNTIFS(Table1[Salary],">30000",Table1[Salary],"<=40000")
=COUNTIFS(Table1[Salary],">40000",Table1[Salary],"<=50000")
=COUNTIFS(Table1[Salary],">50000",Table1[Salary],"<=60000")
=COUNTIFS(Table1[Salary],">60000",Table1[Salary],"<=70000")
=COUNTIFS(Table1[Salary],">70000",Table1[Salary],"<=80000")
=COUNTIFS(Table1[Salary],">80000",Table1[Salary],"<=90000")
=COUNTIFS(Table1[Salary],">90000",Table1[Salary],"<=100000")
=COUNTIFS(Table1[Salary],">39999",Table1[Salary],"<49999")
=COUNTIFS(Table1[Salary],">110000",Table1[Salary],"<=120000")
=COUNTIFS(Table1[Salary],">119999",Table1[Salary],"<=1300000")`

### Results

![Dash](https://github.com/user-attachments/assets/7b5eaa94-5c16-48bb-a2e4-651552b1a4fe)



![salary_page](https://github.com/user-attachments/assets/d0c45aff-6194-4f10-86a6-4c9ed772bbe5)

### Limitation
Generally, there are two genders in the organization. However, some employees 
refused to disclose their gender.  “Others”  was assigned to represent this category. This however, does affect the accuracy and reliability of the insights uncovered in this analysis in any sense.

### Recommendations
- Gender equality is a an healthy organizational culture that will help foster team spirit in employees and promote productivity. Palmoria Group management should create a sustainable payment structure that promotes gender quality.
- Employee rating should never be based on gender and departments but on certification, years of experience, level of degree, years of study, dedication to work, and productivity.
- Compliance to with labour law will give the company a good image and prevent legal altercations. $90,000 minimum wage should be implemented across all the regions. This will help the company reduce turn-over rate and boost employee contribution to organizational growth company-wide.
