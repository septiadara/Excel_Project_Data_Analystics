# Data Science Salary Calculator - Excel Dashboard

> Final Project for Excel for Data Analytics Course by Luke Barousse

### 🔗 Live Dashboard: [View Excel File](./Data_Science_Salary_Calculator.xlsx)
<img width="1105" height="412" alt="1_Salary_Dashboard" src="https://github.com/user-attachments/assets/50d8278e-662b-4f52-8faa-f506d8053672" />

---

### Chapter 1: Introduction

**Objective:** Build an interactive salary calculator to help job seekers estimate data science salaries by Job Title, Country, and Employment Type.

**Dataset:** Data Science Salaries 2023 - 3,000+ job postings from Ladders, Hired, etc.
- Source: Provided by Luke Barousse course
- Fields: Job Title, Country, Employment Type, Median Salary, Job Platform, and Job Count

**Tools Used:** Microsoft Excel - XLOOKUP, AVERAGEIFS, MEDIAN, Data Validation (Dropdown), Bing Maps Chart, Bar Charts

**What I Learned:**
- How to structure raw data for a calculator dashboard
- Using dropdowns as dynamic filters
- Connecting charts to calculated KPIs

---

### Chapter 2: Chart and Map Breakdown

This is a fully dynamic dashboard. When you select a value, everything updates.

**1. Job Title Filter (Left Chart)**
- Bar chart comparing median salary across 10 roles
- The selected title is highlighted in dark blue
- Insight: Senior Data Scientist is the highest paid at $155K in this filter

**2. Country Map (Middle - Powered by Bing)**
- Visual map showing salary distribution by country
- Selected country: United States
- Insight: US, Brazil, Australia, and EU countries dominate high-paying roles

**3. Employment Type (Right Chart)**
- Comparison between Internship, Full-time, Part-time, Temp, Contractor
- Calculated with *FILTER()* function to excludes entries containing "and", coma and zero values.
  ```
  =FILTER(J2#;NOT(ISNUMBER(SEARCH("and";J2#)))*(J2#<>0))
  ```
- Insight: Internship shows surprisingly high avg due to big-tech outliers, but Full-time is the most stable high-payer

**KPIs at Bottom:**
- **Median Salary:** $155,000 - Calculated with:
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
- **Top Job Platform:** Ladders - Most listings for this role
- **Job Count:** 1,437 - Number of jobs matching the filter

---

### Chapter 3: Conclusion

**Key Takeaway:** 
Senior roles in the US as Full-time employees command the highest median salary, but the market is global. This dashboard helps anyone quickly benchmark their offer.

**Challenges I Solved:**
- Handling blank salary fields with IFERROR
- Making the Bing Map work without Power BI
- Syncing 3 different charts to 3 dropdowns

**Credits:** Thank you to Luke Barousse for the amazing Excel for Data Analytics course!

---
*Made with ❤️ by Septia Dara Pratiwi | Semarang, Indonesia | Aspiring Data Analyst*
