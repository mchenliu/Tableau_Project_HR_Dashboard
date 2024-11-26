# Table of Contents
- [Table of Contents](#table-of-contents)
- [Human Resources Dashboard | Overview](#human-resources-dashboard--overview)
- [Human Resrouces Dashboard | Employee Details](#human-resrouces-dashboard--employee-details)
- [Introduction](#introduction)
  - [Tools Used](#tools-used)
- [Steps to Build Dashboards](#steps-to-build-dashboards)
  - [:one: Define User Requirements](#one-define-user-requirements)
  - [:two: Build Data Source](#two-build-data-source)
  - [:three: Build Charts](#three-build-charts)
  - [:four: Dashboard Build](#four-dashboard-build)
- [Conclusion](#conclusion)


# Human Resources Dashboard | Overview
![Overview_Dashboard](/Material/Images/Overview_Dashboard.gif)
# Human Resrouces Dashboard | Employee Details
![Detailed_Dashboard](/Material/Images/Detailed_Dashboard.gif)


# Introduction  
:mega: In this project, I developed two interactive and concise human resources dashboards: **Overview** and **Employee Details**. These dashboards effectively provide key insights into employee demographics, departmental distribution, income levels, performance rating and educational backgrounds.

The project was completed as part of Baraa Salkini's course on [Udemy](https://www.udemy.com/course/the-tableau-ultimate-course-from-zero-to-hero). The dataset used in this project was generated using ChatGPT and the Faker library. 

:mag: Check out my HR dashboard on [Tableau Public](https://public.tableau.com/app/profile/mei.liu4813/viz/HumanResourcesDashboard_17325382179870/DetailDashboard).

## Tools Used
**:art: Tableau:** A powerful tool for creating data visualizations and business intelligence dashboards, enabling insightful analysis and reporting.  
**:pencil2: draw.io:** Used to sketch the container structures for dashboard design.  
**:octopus: Git & Github:** My go-to for version control and tracking my project progress.  

# Steps to Build Dashboards
## :one: Define User Requirements
- **:office_worker: Identify Target Audience:** The dashboard is designed for HR managers, addressing two primary needs:
  1. Overview: Provides high-level insights into key HR metrics.
  2. Employee Details View: Enables detailed exploration of individual employee data.  

- **:globe_with_meridians: Overview:**  
Divided into three sections to provide comprehensive metrics:
  1. Overview: Key HR stats such as hired, active, and terminated employees; department/job breakdowns; HQ vs. branches; and location distribution.
  2. Demographics: Workforce composition by gender, age groups, education levels, and their correlation with performance ratings.
  3. Income Analysis: Salary comparisons by gender and education, and the relationship between age and salary across departments.  
- **:bulb: Employee Details View:**
  1. Detailed list of employees (name, department, position, gender, age, education, salary).
  2. Fully filterable by any column.

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
![BAN](/Material/Images/Ban.png)  
- **:bar_chart: Bar Chart:** Effective for visualizing distributions. In this dashboard, bar charts highlighted departmental distribution and breakdowns of education levels and age groups.
![Bar_Chart](/Material/Images/Bar_Chart.png)  
- **:world_map: Map**: Used to illustrate location hierarchies, detailing relationships between location, state, and city.
![Map](/Material/Images/Map.png)  
- **:pizza: Pie Chart:** Represented gender distribution alongside active vs. terminated employee ratios.
![Pie_Chart](/Material/Images/Pie.png)  
- **:fire: Heat Map:** Highlighted relationships and distributions between dimensions. The highest percentages and counts were visually emphasized. Two heat maps were created to analyz relationships between:: 
  - Age Group vs. Education Level
  - Education Level vs. Performance Rating  
  
*Age Group vs. Education Level*  
![Heat_Map_1](/Material/Images/Heat_Map1.png)  
*Education Level vs. Performance Rating*  
![Heat_Map_2](/Material/Images/Heat_Map2.png)  
- **:red_circle::heavy_minus_sign::white_circle: Barbell Chart:** Revealed the gender pay gap across different education levels, providing a clear view of disparities.  
![Barbell_Chart](/Material/Images/Barbell.png)  
- **:milky_way: Scatter Plot:** Demonstrated the relationship between age and salary, uncovering potential trends and correlations.  
![Scatter_Plot](/Material/Images/Scattor_Plot.png)  

## :four: Dashboard Build

**Overview Dashboard**  

**:bricks: Structure:**
- Navigation Bar: Included logo and navigation icons.
- Header: Contained a dashboard title and filters.
- Charts:  
  - Overview: Displayed employee count, departmental data, and location insights.
  - Demographic: Highlighted gender, education levels, age groups, and performance ratings.
Income Analysis: Explored salary distributions by gender and education level.
  - Income Analysis: Discovered correlation between education level, gender and salary

**:paintbrush: Design and Build:**
- **Planned and sketched** the layout in draw.io, defining container structures for clarity.
- Integrated charts into the Overview Dashboard.
- Refined the dashboard's design, including colors, text styles, and inner/outer spacing for a polished look.
- Added filters, dynamic tooltips, and performed thorough testing.
- Enhanced charts with hierarchies, enabling drill-down functionality and incorporating them into tooltips.
- Added logos and icons to the navigation bar for a cohesive and branded design.

*Define different objects in the sketch*  
![Dashboard1_2](/Material/Images/Dashboard1_2.png)  
*Overview Dashboard sketch*  
![Dashboard1_1](/Material/Images/Dashboard1_1.png)  
*Detail design for chart containers*  
![Dashboard1_3](/Material/Images/Dashboard1_3.png)  
*Dynamic tooltips*
![Tooltip1](/Material/Images/Tooltip_1.gif)  
*Tooltips with a drilled-down list*  
![Tooltip2](/Material/Images/Tooltip_2.gif) 


**Employee Details Dashboard**  

**:bricks: Structure:**
- Navigation Bar: Same as Overview Dashboard.
- Header: Simplified without filters.
- Filters: Added seven interactive filters above the employee details list.
- Detail Section: Listed employee information with drill-down capabilities.  

**:paintbrush: Design and Build:**
- Created a sketch in draw.io for layout consistency.
- Integrated filters to enhanced interactivity.
- Added navigation buttons to facilitate seamless switching between the two dashboards.

*Detail list Dashboard sketch*  
![Employee_details_sketch](/Material/Images/Employees_Details_Sketch.png)  
*Filter design*  
![Filter_desgin](/Material/Images/Filter_Design.png)  
*Switching between dashboards*  
![Navigation](/Material/Images/Navigation.gif)  

# Conclusion
This project successfully demonstrates the development of two interactive and insightful human resources dashboards: Overview and Employee Details. Using Tableau and draw.io, I transformed HR data into a powerful decision-making tool for HR managers. These dashboards offer:
- High-Level Insights: The Overview Dashboard provides a comprehensive view of key HR metrics, including employee demographics, departmental breakdowns, performance ratings, and income analysis.
- Detailed Exploration: The Employee Details Dashboard enables an in-depth analysis of individual employee data, supported by dynamic filters and drill-down capabilities.  
  
By combining structured design, effective visualizations, and interactivity, this project achieves its goal of simplifying HR data analysis and delivering actionable insights. The process highlights key skills in data preparation, visualization, and user-centric dashboard design.

:mag: Explore the full dashboards on [Tableau Public](https://public.tableau.com/app/profile/mei.liu4813/viz/HumanResourcesDashboard_17325382179870/DetailDashboard).