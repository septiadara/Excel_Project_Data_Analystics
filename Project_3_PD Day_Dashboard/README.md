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

## 🔧 Data Cleaning: 
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

## 🔍 Analysis: More Than Just The Highest Number

To find the best date for a national conference, I created a Pivot Table: `Count of Schools by PD Date`.

Initial finding - Top 10 most frequent PD dates:  
<img width="216" height="220" alt="21_Top_Ten" src="https://github.com/user-attachments/assets/0214508b-c87d-41b1-b518-c088e6bedd2f" />

But when I broke it down by Province or Territory, I found a problem: these Top 10 dates were concentrated in only 3-5 provinces (mostly Alberta, British Columbia, Quebec, and Ontario). That doesn't meet the client's goal of a *cross-Canada* conference.

So I expanded to Top 20 and looked for a better balance between:
1.  High number of eligible schools
2.  Wide geographic distribution (10 provinces + 3 territories)

My shortlisted dates with best balance:
- **20 November 2026 (73 schools)** - distributed across 6+ regions including Northwest Territories & New Brunswick
- **16 April 2027 (54 schools)** - 8 regions including Prince Edward Island, Northwest Territories, Nunavut
- **19 February 2027 (47 schools)** - 7 regions from East to West

**Decision:** Instead of just taking the Top 10 by count, I combined high-frequency dates with dates that have broader provincial coverage. This ensures the conference can attract teachers from across Canada, not just a few provinces.

## 📊 Dashboard & Final Recommendation

I built an interactive dashboard in Excel to help the client decide.

**Key Metrics:**
- Top Ten Recommendation Dates
- Eligible Schools on Selected Date
- Percentage of Participation 
- Total Schools in Database 

**Top 10 Recommendation Dates:**
Created a dropdown list so client can click any date and see the province breakdown. 
<img width="156" height="231" alt="22_Top_Ten_2" src="https://github.com/user-attachments/assets/f3d8f3d1-d01d-4b2d-9d37-a13a7290bbb2" />

### ✅ Final Recommendation: 16 April 2027

**Why not the highest count (23 Oct 2026 - 99 schools)?**
Because 23 Oct is concentrated in only a few provinces. 49 British Columbia, 21 Manitoba, 14 Alberta, 6 Quebec, 6 Nova Scotia, 3 Territories.

It fails the client's main goal: national participation.

**Why 16 April 2027 is the best balance:**
- **54 schools** can attend.
- **Geographically diverse:** 17 Ontario, 10 Quebec, 10 Manitoba, 8 BC, 6 Alberta, 1 NWT, 1 Saskatchewan, 1 Prince Edward Island = 8 regions from West to East
- **Spring timing:** Ideal for a conference (not start or end of school year rush like August/September)

This date maximizes both attendance and national representation.

## 💡 What I Learned
This project taught me the full cycle: Web Research -> Messy Entry Data -> ETL with Power Query (Unpivot Column) -> Pivot Analysis -> Storytelling with Dashboard. And that the highest number is not always the best answer - distribution matters.


