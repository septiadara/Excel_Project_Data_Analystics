# Data Science Salary Calculator - Excel Dashboard

> Final Project for Excel for Data Analytics Course by Luke Barousse

### 🔗 Live Dashboard: [View Excel File](./Data_Science_Salary_Calculator.xlsx)
<img width="1105" height="412" alt="1_Salary_Dashboard" src="https://github.com/user-attachments/assets/50d8278e-662b-4f52-8faa-f506d8053672" />

---

### Chapter 1: Introduction

**Objective:** Build an interactive salary calculator to help job seekers estimate data science salaries by Job Title, Country, and Employment Type.

**Dataset:** Data Science Salaries 2023 - 3,000+ job postings from Ladders, Hired, etc.
- Source: Provided by Luke Barousse course
- Fields: Job Title, Job Platform, Schedule Type, Job Location, Country, Posted Date, Employment Type, Year Average and Skills.

**Tools Used:** Microsoft Excel - XLOOKUP, COUNTIF, MEDIAN, SORT, Data Validation (Dropdown), Bing Maps Chart, Bar Charts

**What I Learned:**
- How to structure raw data for a calculator dashboard
- Using dropdowns as dynamic filters
- Connecting charts to calculated KPIs

---

### Chapter 2: Chart and Map Breakdown

This is a fully dynamic dashboard. When you select a value, everything updates.

**1. Job Title Filter (Left Chart)**

<img width="554" height="346" alt="3_Left_Chart" src="https://github.com/user-attachments/assets/5bab955f-681d-4450-aa1d-e260a41bbdfc" />


- Bar chart comparing median salary across 10 roles
- The selected title is highlighted in dark blue
- Insight: Senior Data Scientist is the highest paid at $155K in this filter

**2. Country Map (Middle - Powered by Bing)**

<img width="591" height="333" alt="4_Middle_Chart" src="https://github.com/user-attachments/assets/bfd54586-b77f-47f4-9c94-1c93dd8f0f06" />


- Visual map showing salary distribution by country
- Insight: US, Brazil, Australia, and EU countries dominate high-paying roles

**3. Employment Type (Right Chart)**

<img width="617" height="329" alt="5_Right_Chart" src="https://github.com/user-attachments/assets/d9884667-6d87-4fe0-ba08-01267a5ebf66" />


- Comparison between Internship, Full-time, Part-time, Temporary Work, Contractor
- Calculated with *FILTER()* function to excludes entries containing "and", coma and zero values.
  ```
  =FILTER(J2#;NOT(ISNUMBER(SEARCH("and";J2#)))*(J2#<>0))
  ```
- Insight: Internship shows surprisingly high avg due to big-tech outliers, but Full-time is the most stable high-payer

**KPIs at Bottom:**
- **Median Salary:** Returns the median salary based on job title, country, and type specified. Calculated with:
    ```
  =MEDIAN(
  IF(
    (jobs[job_title_short]=A2)*
    (jobs[job_country]=country)*
    (ISNUMBER(SEARCH(type,jobs[job_schedule_type])))*
    (jobs[salary_year_avg]<>0),
    jobs[salary_year_avg]
  )
  )
  ```
- **Top Job Platform:** Shows the most job platform from the list, calculated with *SORT()* function.
- **Job Count:** Show the number of jobs matching the filter, calculated with:  
  ```
  =XLOOKUP(title;D2:D11;E2:E11;"No Results")
  ```
  <img width="433" height="239" alt="2_XLOOKUP_function" src="https://github.com/user-attachments/assets/86cc85ad-ba0a-4174-a14f-fb764316d2a2" />


---

### Chapter 3: Conclusion

**Challenges I Solved:**
- Handling blank salary fields with IFERROR
- Making the Bing Map work without Power BI
- Syncing 3 different charts to 3 dropdowns

**Credits:** Thank you to Luke Barousse for the amazing Excel for Data Analytics course!

---
*Made with ❤️ by Septia Dara Pratiwi | Semarang, Indonesia | Aspiring Data Analyst*
