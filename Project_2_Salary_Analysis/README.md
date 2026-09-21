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

      <img width="361" height="506" alt="12_Unpivot_Columns" src="https://github.com/user-attachments/assets/83ef5dd5-ba07-4d5f-8b79-5419d499f1e4" /> <img width="350" height="524" alt="11_data_jobs_skills" src="https://github.com/user-attachments/assets/c2e14247-40f1-4b7d-b1f1-ac5b12ca69ec" />

4.  **Data Modeling:** Created a relationship between two tables using `job_id` as the key.
   
       <img width="540" height="377" alt="15_Relationship" src="https://github.com/user-attachments/assets/ae2b429e-a825-4f49-bb2f-ea3cc5c30963" />

5.  Loaded data to Data Model (not just to sheet) to use DAX and Pivot Tables

**Tools Used:** Excel Power Query, Data Model, Pivot Table, DAX, Relationship

---

### Chapter 2: Chart and Map - The Analysis

I created 4 analysis sheets using Pivot Tables + DAX:

**Analysis 1: Salary vs. Skills**
- Question: Do people with more skills get higher salary?
- Method: Used `AVERAGEX` and `COUNT` in DAX
- Chart: Scatter plot / Bar chart showing average salary by number of skills
- Insight: [Write your finding - e.g., Salary increases up to 5 skills, then plateaus]

**Analysis 2: Median Salary - US vs. Non-US**
- Question: Is US really paying more?
- Method: Created DAX measure `Median Salary = MEDIAN([salary])` and grouped by Country = US vs. Non-US
- Chart: Column chart comparing US vs. Non-US
- Insight: [e.g., US median is 20% higher than Non-US]

**Analysis 3: Top Skills for Data Nerds**
- Question: What are the most demanded skills?
- Method: Pivot Table on unpivoted skills table, sorted by count
- Chart: Horizontal bar chart of Top 10 skills
- Insight: [e.g., SQL, Python, and Excel are Top 3 - SQL is still #1]

**Analysis 4: Salary Analysis with Crossfilter**
- Question: How does one skill affect salary?
- Method: Used Slicers as crossfilters - when you click a skill, all charts filter
- Chart: Interactive dashboard with slicers
- Insight: [e.g., Knowing Spark or AWS increases median salary significantly]

---

### Chapter 3: Conclusion

**Key Takeaway:** 
Data cleaning is 70% of the work. By using Power Query to unpivot skills and creating a relationship with job_id, I could answer complex questions that are impossible with normal Excel formulas.

**Challenges I Solved:**
- Unpivoting 15+ skill columns into clean rows
- Understanding why to load to Data Model vs. Worksheet
- Writing my first DAX measures for median and average
- Using relationships instead of VLOOKUP

**What I Learned:**
This project taught me the real workflow of a Data Analyst: Extract -> Transform (Power Query) -> Model (Relationship) -> Analyze (Pivot + DAX).

**Next Improvement:** I want to redo this analysis in Power BI with the same data model.

---
*Project by [Your Name] | From Semarang, Indonesia | Excel to Power BI Journey*
