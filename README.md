# Table of Contents
- [Table of Contents](#table-of-contents)
- [Human Resources Dashboard | Overview](#human-resources-dashboard--overview)
- [Human Resrouces Dashboard | Details](#human-resrouces-dashboard--details)
- [Introduction](#introduction)
  - [Tools Used](#tools-used)
- [Steps to Build Dashboards](#steps-to-build-dashboards)
  - [:one: Define User Requirements](#one-define-user-requirements)
  - [:two: Build Data Source](#two-build-data-source)
  - [:three: Build Charts](#three-build-charts)
  - [:four: Dashboard Build](#four-dashboard-build)
  - [Conclusion](#conclusion)
  - [What I Learned](#what-i-learned)


# Human Resources Dashboard | Overview
![Overview_Dashboard](/Material/Images/Overview_Dashboard.gif)
# Human Resrouces Dashboard | Details
![Detailed_Dashboard](/Material/Images/Detailed_Dashboard.gif)


# Introduction  
:mega: In this project, I developed two interactive and concise human resources dashboards: Overview and Employee Details. These dashboards effectively provide key insights into employee demographics, departmental distribution, income levels, and educational backgrounds.

The project was completed as part of Baraa Salkini's course on [Udemy](https://www.udemy.com/course/the-tableau-ultimate-course-from-zero-to-hero). The dataset used in this project was generated using ChatGPT and the Faker library. 

:mag: Check out my HR dashboard on [Tableau Public](https://public.tableau.com/app/profile/mei.liu4813/viz/HumanResourcesDashboard_17325382179870/DetailDashboard).

## Tools Used
**:art: Tableau:** A powerful tool for creating data visualizations and business intelligence dashboards, enabling insightful analysis and reporting. 
**:pencil2: draw.io:** Used to sketch the container structures for dashboard design.
**:octopus:Git & Github:** My go-to for version control and tracking my project progress.
___
# Steps to Build Dashboards
## :one: Define User Requirements
- Identified the needs of the target audience and outlined the key metrics and visualizations to be included in the dashboards.
## :two: Build Data Source
- Connected the dataset to Tableau and conducted an initial inspection to verify data quality and ensure accurate data type mapping.
- Explored the data using Tableau worksheets to understand relationships and potential insights.
## :three: Build Charts
- **Chart Selection:** Analyzed user requirements to select the most effective chart types for presenting data.
- **Template Design:** Created a reusable template defining the following:
  - Colors: `#03c4a1`, `#c52a87`, `#777777` and `#f5f5f5`
  - Font: Trebuchet MS
  - Background: Dark theme

- Developed **calculated fields** to enhance chart functionality
  - Employee Location: Categorized locations into HQ and branches.
  - Age Groups: Grouped employees into age ranges.
  - Highlighting: Created dynamic highlights for top metrics.  

*1. Employee Location:*
```
CASE [State]
    WHEN 'New York' THEN 'HQ
    ELSE 'Branch'
END
```
*2. Total Employee Terminated:*
```
COUNT(
    IF NOT ISNULL([Termdate])
    THEN[Employee ID]
END)
```
*3. Age:*
```
DATEDIFF('year',[Birthdate],TODAY())
```
*4. Employee Age Group:*
```
IF [Age] < 25 THEN '<25'
ELSEIF [Age] >=25 AND [Age] < 35 THEN '25-35'
ELSEIF [Age] >=35 AND [Age] < 45 THEN '35-45'
ELSEIF [Age] >=45 AND [Age] < 55 THEN '45-55'
ELSEIF [Age] >=55 THEN '55+'
END
``` 
*5. Highlight Max:*
```
WINDOW_MAX([Total Hired]) = [Total Hired]
```
*6. Highlight Top 2 Job Titles:*
```
RANK([% Total Hired]) <= 2
```

___
**Charts Used**
Each chart type was selected for its ability to effectively communicate specific insights:
- **:chart_with_upwards_trend: BAN (Big Ass Numbers) + Line Chart:** Ideal for presenting KPIs at a glance. I combined BANs with line charts to show KPIs and trends for active vs. terminated employees over time.
![BAN](/Material/Images/BANs.png)  
- **:bar_chart: Bar Chart:** Effective for visualizing distributions. In this dashboard, bar charts highlighted departmental distribution and breakdowns of education levels and age groups.
![Bar_Chart](/Material/Images/Bar_Chart_Department.png)  
- **:globe_with_meridians: Map**: Used to illustrate location hierarchies, detailing relationships between location, state, and city.
![Map](/Material/Images/Map_Location.png)  
- **:pizza: Pie Chart:** RRepresented gender distribution alongside active vs. terminated employee ratios.
![Pie_Chart](/Material/Images/Pie_Gender.png)  
- **:fire: Heat Map:** Highlighted relationships and distributions between dimensions. The highest percentages and counts were visually emphasized. Two heat maps were created to analyz relationships between:: 
  - Age Group vs. Education Level
  - Education Level vs. Performance Rating  
  
*Age Group vs. Education Level*  
![Heat_Map_1](/Material/Images/Heat_Map_1.png)    
*Education Level vs. Performance Rating*  
![Heat_Map_2](/Material/Images/Heat_Map_2.png)  
- **:red_circle::heavy_minus_sign::white_circle: Barbell Chart:** Revealed the gender pay gap across different education levels, providing a clear view of disparities.  
![Barbell_Chart](/Material/Images/Barbell_Chart.png)  
- **:milky_way: Scatter Plot:** Demonstrated the relationship between age and salary, uncovering potential trends and correlations.  
![Scatter_Plot](/Material/Images/Scatter_Plot.png)  
## :four: Dashboard Build

**Overview Dashboard**
**:construction: Structure:**
- Navigation Bar: Included logo and navigation icons.
- Header: Contained a dashboard title and filters.
- Charts:  
  - Overview: Displayed employee count, departmental data, and location insights.
  - Demographic: Highlighted gender, education levels, age groups, and performance ratings.
Income Analysis: Explored salary distributions by gender and education level.
  - Income Analysis: Discovered correlation between education level, gender and salary

**:paintbrush: Design and Build Process:**
**Planned and sketched** the layout in draw.io, defining container structure for clarity.
Pulled charts into Tableau, ensuring dynamic tooltips and interactivity.
Added calculated fields for enhanced chart presentation.

*Define different objects in the sketch*  
![Dashboard1_2](/Material/Images/Dashboard1_2.png)  
*Overview Dashboard sketch*  
![Dashboard1_1](/Material/Images/Dashboard1_1.png)  
*Detail design for chart containers*  
![Dashboard1_3](/Material/Images/Dashboard1_3.png)  

**Employee Details Dashboard**
**:construction: Structure:**
- Navigation Bar: Same as Overview Dashboard.
- Header: Simplified without filters.
- Filters: Added seven interactive filters above the employee details list.
- Detail Section: Listed employee information with drill-down capabilities.  

**:paintbrush: Design and Build Process:**
Created a sketch in draw.io for layout consistency.
Integrated filters and dynamic calculated fields into Tableau for enhanced interactivity.



*Detail list Dashboard sketch*  
![Employee_details_sketch](/Material/Images/Employees_Details_Sketch.png)  
*Filter design*  
![Filter_desgin](/Material/Images/Filter_Design.png)



## Conclusion
## What I Learned
