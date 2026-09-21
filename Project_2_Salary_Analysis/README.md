# Data Jobs Salary & Skills Analysis - Power Query & DAX

> Final Advanced Project - Excel for Data Analytics by Luke Barousse

### 🔗 Live File: [View Excel Workbook](2_Salary_Analysis.xlsx)

---

### Chapter 1: Introduction

**Objective:** To analyze the relationship between data job salaries and required skills. 

**The Problem:** The raw data was messy. I needed to clean it before analysis.

**My Process - Data Cleaning (Power Query):**
1.  Connected to Excel source and launched Power Query Editor
2.  **Cleaned Data:** Changed column types (salary to currency, job posted date to date), trimmed whitespace, cleaned text, reordered columns
3.  **Created Two Queries:**
    - `data_job_salary`: Clean table for salary information
    - `data_job_skills`: Unpivoted the job skills columns so each skill is in its own row (from wide to long format)

      <img width="361" height="506" alt="12_Unpivot_Columns" src="https://github.com/user-attachments/assets/83ef5dd5-ba07-4d5f-8b79-5419d499f1e4" /> <img width="349" height="507" alt="11_data_jobs_skills" src="https://github.com/user-attachments/assets/1b890e19-b84d-4139-abd6-d93fc49ee138" />


4.  **Data Modeling:** Created a relationship between two tables using `job_id` as the key.
   
       <img width="540" height="377" alt="15_Relationship" src="https://github.com/user-attachments/assets/ae2b429e-a825-4f49-bb2f-ea3cc5c30963" />

5.  Loaded data to Data Model (not just to sheet) to use DAX and Pivot Tables

**Tools Used:** Excel Power Query, Data Model, Pivot Table, DAX, Relationship

---

### Chapter 2: Chart and Map - The Analysis

I created 4 analysis sheets using Pivot Tables + DAX:

**Analysis 1: Salary vs. Skills**
- Question: Do people with more skills get higher salary?
- Method: Used `MEDIAN` and `COUNT` in DAX
- Chart: Scatter plot showing median salary by average skills required
  <img width="1652" height="993" alt="13_Salary_Vs_Skills" src="https://github.com/user-attachments/assets/6514f620-53c9-4220-92bd-1ef5ef84c4f5" />

- Insight: Dotted line goes up, which means more skills equal more money, particularly in roles like Senior Data Engineer and Senior Data Scientist. Roles, such as Data Analyst and Business Analyst, require few skills and offer low salary.

**Analysis 2: Median Salary - US vs. Non-US**
- Question: What’s the salary for data jobs in different regions?
- Method: Created DAX measure for:
   
  calculating median year salary
       
  `Median Salary = MEDIAN(data_jobs_salary[salary_year_avg])`
    
  and grouping for US and Non-US countries by using *CALCULATE()* funtion
     
  `Median Salary Non-US = CALCULATE([Median Salary];data_jobs_salary[job_country]<>"United States")`
  
- Insight: Both Senior Data Engineer and Data Scientist reach higher median salary both in US and internationally.
  <img width="753" height="289" alt="7_Median_Salary_US_Vs_NonUS" src="https://github.com/user-attachments/assets/5a00e16f-324d-493e-a0ad-b1a45f15c460" />
 
    
**Analysis 3: Top Skills for Data Nerds**
- Question: What are the most demanded skills?
- Method: Pivot Table on unpivoted skills table, sorted by count
- Chart: Bar chart of Top 10 skills  
  <img width="1629" height="993" alt="16_Top_Skills" src="https://github.com/user-attachments/assets/b61ef25a-6ae6-4458-868d-9d916031179c" />

- Insight: More than half of all data-related job need SQL and Python, while Power BI is in the last position because it focuses on engineering or science roles.

**Analysis 4: Salary Analysis with Crossfilter**
- Question: How does one skill affect salary?
- Method: Used `CROSSFILTER()` funtion to filter median salary by skills, and vice verca.  

  `Median Salary by Skills = CALCULATE([Median Salary];CROSSFILTER(data_jobs_salary[job_id];data_jobs_skills[job_id];Both))`
  
- Chart: Combo chart to plot median salary and skill likelihood (%) from my PivotTable.
  <img width="1002" height="381" alt="17_Salary_Analysis" src="https://github.com/user-attachments/assets/bedb4515-53a8-4a3c-8cf8-c6a58dd7b0b5" />

- Insight: Python, SQL and Excel become the most demand skill for Data Analyst job in the US, but Python and Oracle get the top highest pay as these data-related job.

---

### Chapter 3: Conclusion

**Key Takeaway:** 
Data cleaning is 70% of the work. By using Power Query to unpivot skills and creating a relationship with job_id, I could answer complex questions that are impossible with normal Excel formulas.

**Challenges I Solved:**
- Unpivoting 15+ skill columns into clean rows
- Understanding why to load to Data Model vs. Worksheet
- Writing my first DAX measures for median, calculate and crossfilter
- Using relationships instead of VLOOKUP

**What I Learned:**
This project taught me the real workflow of a Data Analyst: Extract -> Transform (Power Query) -> Model (Relationship) -> Analyze (Pivot + DAX).

---
*Project by Septia Dara Pratiwi | From Semarang, Indonesia | Aspiring Data Analyst*
