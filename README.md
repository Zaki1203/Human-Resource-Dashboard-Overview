# Human-Resource-Dashboard-Overview

## Project Overview   
This HR Dashboard project, built using Tableau, provides a centralized and interactive platform to analyze workforce metrics across four key areas: Overview, Demographics, Income, and Employee Records. It tracks hiring and termination trends, evaluates gender and education diversity, analyzes income disparities, and offers a detailed employee directory. The dashboard supports strategic HR decisions through interactive visuals, calculated fields, and dynamic filters, helping identify workforce trends, performance insights, and organizational structure distribution.
##  Project Objective 
The primary objective of this HR Dashboard is to deliver a centralized, interactive platform for monitoring, analyzing, and understanding key HR metrics. The dashboard is structured into four main sections — Overview, Demographics, Income, and Employee Records View — each tailored to support strategic HR decision-making and workforce analysis.

### 1. **Overview**
- Display the **total number of hired, active, and terminated employees** to give a snapshot of current workforce dynamics.
- Visualize **hiring and termination trends over the years** to identify recruitment and attrition patterns.
- Provide a **breakdown of total employees by department and job title** to understand organizational structure.
- **Compare the workforce size** between **headquarters (New York)** and branch offices to monitor distribution.
- Show **employee distribution by city and state** to assess geographic spread and location-based workforce trends.

### 2. **Demographics**
- Present the **gender ratio** to evaluate gender diversity across the organization.
- Visualize the **distribution of employees by age groups and education levels** to analyze workforce composition.
- Show total employees in each age group and each education level** to identify talent demographics.
- Explore the relationship between educational background and performance ratings to assess talent quality and educational impact.

### 3. Income
- *Compare salaries across education levels and genders to detect any income disparities or trends.
- Analyze the correlation between age and salary within each department to assess compensation fairness and trends across age groups.

### 4. Employee Records View
- Provide a comprehensive, filterable table of all employees containing key information such as:
  - Name
  - Department
  - Position
  - Gender
  - Age
  - Education
  - Salary
  - Enable users to filter and sort employee data by any column, supporting deeper individual and group-level analysis.

##  Dataset 
Dataset has been generated using Chatgbt,here is the link of the dataset with icons used for the dashboard [click here](

## Tools 
I've utlized Tableau  for basic data inspection and creating interactive dashboard

## Data Preparation

**Step-by-Step Process:**

1. **Unzip the Folder**:  
   Start by unzipping the folder containing the Human Resource dataset.

2. **Open in Excel**:  
   Open the Excel file to perform initial data cleaning:
   - Remove any duplicate rows.
   - Check for missing or inconsistent data.
     
3. **Import into Tableau**:  
   Drag and drop the cleaned Excel file into Tableau.

4. **Inspect Data Types**:  
   In Tableau’s data source tab:
   - Review the data types of each column (e.g., string, number, date).
     
5. **Open Worksheet**:  
   After confirming the data is ready, click on the worksheet tab to begin your visual analysis.

## Calculated Field 
I have created calculated fields as follows

Total Hired= COUNT([Employee ID])

TOtal Terminated =COUNT(if not isnull ([Termdate]) THEN [Employee ID]END)

Total Active =COUNT(IF  isnull ([Termdate]) THEN [Employee ID]END)

Length of Hire =if ISNULL([Termdate]) then
DATEDIFF('year',[Hiredate],TODAY())
ELSE DATEDIFF('year',[Hiredate],[Termdate])
END

Age= DATEDIFF('year',[Birthdate],TODAY())

% Total Hired =[Total Hired] / TOTAL([Total Hired])

Max= WINDOW_MAX([Total Hired])=[Total Hired]

% Max=WINDOW_MAX([% Total Hired])=[% Total Hired]

Fullname=[First Name]+ ' ' + [Last Name]

Location =CASE [State]
     WHEN 'New York' THEN 'HQ'
     ELSE 'Branches'
END

Status = if ISNULL([Termdate]) then 'Hired'
ELSE 'Termidated'
END

## WorkBook Format

1. Trebuchet MS font is used with a font size of 9.  
2. All gridlines from rows, columns, and the sheet are removed.  
3. The background features a custom black color (#171717).  
4. The color palette includes #777777, #03c4a1, #c52a87, and #ffffff.

Both action filters and standard filters have been implemented to enhance interactivity and allow users to explore data dynamically


## Key Insights 


1. The company currently has **7,984 active employees**.  
2. A total of **966 employees have been terminated**.  
3. **8,950 employees have been hired** overall.  
4. The majority of hires were in **Operations (2,429)**, followed by **Sales (1,634)**, **Customer Service (1,489)**, and **IT (1,243)**.  
5. **70% of employees were hired at the Headquarters in New York**, indicating a major concentration of the workforce there.  
6. The highest number of hires occurred in **2017 with 1,560 employees**. However, hiring declined consistently until 2021.  
7. Since **2018**, there has been a **rise in employee terminations**, peaking in **2023 with 174 terminations**.  
8. **West Virginia recorded the lowest termination rate** among all states.  
9. **54% of male employees were hired**, with **11% of them eventually terminated**.  
10. **46% of female employees were hired**, with **11% also terminated**, indicating parity in termination rates across genders.  
11. Employees with a **High School education level tend to earn lower salaries**, whereas those with a **PhD earn the highest average salaries**.  
12. Employees aged **35–44 with a Bachelor's degree have the highest termination rate** among educational groups.  
13. The role of **Financial Manager commands the highest above-average salary**, while **HR Assistants earn below-average salaries**.  
14. **85% of employees with only a High School education fall under the 'Needs Improvement' performance category**, while **Bachelor’s degree holders are mostly in the 'Average' (55%)**, and **Master’s and PhD holders predominantly fall into the 'Excellent' category**.


