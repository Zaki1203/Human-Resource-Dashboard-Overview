# Human-Resource-Dashboard-Overview

## Project Overview 
The HR Analytics Dashboard is a comprehensive reporting solution designed to provide both high-level insights and detailed analysis of employee data within the organization. The dashboard consolidates key HR metrics into an intuitive and interactive format, supporting strategic decision-making and workforce planning.

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

