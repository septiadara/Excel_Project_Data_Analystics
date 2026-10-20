# Buleleng Rainfall Analysis 2015 – 2024
Objective: This project is part of my work as a freelance geology data analyst. To analyze the relationship between rainfall intensity and disaster occurrence in Buleleng, Bali.

### Key Findings
Buleleng experienced an increase in the average of max daily rainfall, from 62 mm in 2019 to 79 mm in 2022, with the emergence of >75 mm precipitation events starting in 2020. In 2020 and 2023, similar max daily intensity (77mm) resulted in only 3-4 disaster, while in 2022,  it resulted in 59 disasters. Extreme rainfall intensity alone doesn’t explain disasters, topography and other environmental factors do.

### Data Source
This analysis combines 3 data sources:
1. CHIRPS Daily Rainfall 2015 – 2024 
2. DIBI (Indonesian Disaster Information Data)
3. BPBD (Regional Disaster Management Agency) Buleleng 2022 (manual collection)

### Tools
Excel Power Query, Power Pivot, DAX, Pivot Charts, DEMNAS 8m, QGIS for slope classification

### My Process
#### 1. Data Cleaning in  Power Query  
•	Connected to the csv file and launched Power Query Editor.  
•	Cleaned and standardized precipitation data in Power Query.  
•	Added a conditional column to modify the month (1 to January, 2 to February, etc).  
•	Changed column types (date to Date, year to Year).  
•	Removed and reordered columns.  <img width="643" height="506" alt="1_Data Cleaning" src="https://github.com/user-attachments/assets/fe32fd72-d222-4ed8-9f84-32efb6aef182" />

#### 2. Data Modelling (Year as key)
In a blank workbook, I connected some tables from all different data sources using Power Pivot to create a data model. After successfully bringing all the data into a data model, now I can define relationships between my tables. 
All the data are associated with year, so I established the relationship between two tables using Year as the key.  <img width="539" height="404" alt="image" src="https://github.com/user-attachments/assets/5e022f84-cda1-4fd1-99ad-0bc5457070b5" />

#### 3. Four Analyses (Trend, Outlier and Correlation)
I created 5 analysis charts using Pivot Table and DAX.
  
#### Analysis 1: The Trend of Extreme Rainfall: Increasing in Intensity and Frequency
<img width="1653" height="993" alt="3_Max Daily Intensity Trend" src="https://github.com/user-attachments/assets/f600c6e7-c5dc-4a98-a550-67a167869a59" />
  
The average of max daily increased from 62 mm up to 79 mm in 2022; and there was an emergence of >75 mm events started from 2020 to 2023.

#### Analysis 2: Does Higher Intensity Mean More Disaster?  
<img width="1653" height="993" alt="4_Max Daily vs Total Disaster" src="https://github.com/user-attachments/assets/4cb7b8d2-12c6-4e26-9db8-b07287a969e4" />

In 2022, it was true that the average of max daily rainfall appeared to be the highest, at 79 mm and the total disaster showed the largest number, at 59 disasters. But how about the other year, with the same amount of max daily rainfall.

### Analysis 3: Why same rainfall intensity doesn’t mean same disaster?  
<img width="1653" height="993" alt="5_Outlier" src="https://github.com/user-attachments/assets/0022e5b9-5d84-415f-9d76-4d8f212d923d" />

The outlier 2022 red dot proved correlation is not just about max daily value. In 2020 and 2023, the average of max daily showed number of 77 mm, but it had only 3 to 4 disasters. In 2022, with the same intensity, Buleleng experienced such an increase in floods and landslide disasters. To show the correlation, I manually collected flood and landslide data from BPBD data source in Buleleng, 2022.

#### Analysis 4: Why so many floods and landslides in 2022?
<img width="1653" height="993" alt="6_2022 Disaster Occured at Rainfall Peaks" src="https://github.com/user-attachments/assets/ce0ac0a0-f605-4f19-a03b-4a69530e6464" />
  
This chart shows that January to March was the peak of the rainy season. Soil already saturated with water from those months, triggering floods and landslides. After dry season (May – September), the first heavy rain in October hit cracked soil that could not absorb water, causing flash floods.

#### 4. Spatial Map  
To get a deep understanding about what happened in Buleleng in 2022, I plotted the data manually on the spatial map using DEMNAS 8m (not exact coordinates, source: BPBD Buleleng 2022) and classified the slope.
<img width="6287" height="4440" alt="7_Spatial Map" src="https://github.com/user-attachments/assets/03fcd004-d5af-4323-85cb-5f921c9c257e" />
      
Based on the topographic map, Buleleng is divided into three zones: the northern coastal region (0-8° flat), a transitional zone (8-15° undulating), and the southern mountainous region (>25° steep). According to BPBD data from 2022, 18 flood events were concentrated in the northern flat region, while 22 landslide events occurred in the steep southern area. Although rainfall peaks in January-March and October-December saturate the soil and reduce shear strength — triggering landslides in the highlands — rivers flow from south to north, transferring flood risk to the coastal plain. This risk is exacerbated by clogged drainage, land-use change, and deforestation.
