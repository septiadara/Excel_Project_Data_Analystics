# Canada Professional Development Day Analysis 2026/2027

## 📖 Introduction
This project is part of my work as a freelance Data Analyst.

A client who organizes an annual teacher conference across Canada asked for help to build a database of Professional Development (PD) Days. The idea is simple: find the best date for a national conference where teachers from all over Canada can join, not just from one or two provinces.

The challenge:
- We need to collect PD Day dates for schools across **10 provinces and 3 territories** of Canada for the **2026/2027 school calendar**.
- Each school district publishes its calendar in a different format on its website.
- My initial data collection was in a messy, wide format - one column for each month (August, September, October, etc) with day numbers inside. Very hard to analyze.  
  <img width="1047" height="417" alt="19_Raw_Data" src="https://github.com/user-attachments/assets/1bdf11f0-49a4-4f19-b4d5-19166f31f64a" />

Client Goal: 
Avoid scheduling the national conference on a day that clashes with many local PD Days, so participation can be truly national.

## 🔧 Data Cleaning
Before I learned Excel for Data Analytics, I would have cleaned this manually... forever 😱

After learning **ETL (Extract, Transform, Load) with Power Query** from Luke Barousse's free resources, I did it in minutes.

**What I did:**
1. **Extract:** Excel file with web research data from school district websites across Canada.
2. **Transform:**
   - In Power Query Editor, I used **Unpivot Column** to transform the 12 month columns into two clean columns: `Day` and `Month`.
   - Changed data type to date.
   - Added **Conditional Column** to add year 2026 from August to December, and add year 2027 from January to July.
   - Added **Costum Column** to combine day, month and year, with formula below:
     
     ```
     Date.FromText(Text.From([Day]) & " " & [Month] & " " & Text.From([Year]), [Culture="en-US"])
     ```
4. **Load:** Loaded the clean, long-format table (2800+ rows) ready for analysis.
   <img width="1129" height="525" alt="20_ETL_Tool" src="https://github.com/user-attachments/assets/c42de865-47a7-4b0c-9ad0-eb153f0f2d86" />




