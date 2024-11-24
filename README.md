# :construction: WORK IN PROGRESS :construction:
___
Check Dashboard [here](https://public.tableau.com/app/profile/mei.liu4813/viz/HR_Dashboard_17323664879310/HRDashboard?publish=yes)
## Table of Contents
- [:construction: WORK IN PROGRESS :construction:](#construction-work-in-progress-construction)
  - [Table of Contents](#table-of-contents)
  - [Human Resources Dashboard](#human-resources-dashboard)
  - [Introduction](#introduction)
  - [Tools I Used](#tools-i-used)
  - [User Story](#user-story)
- [Steps to Build Dashboard](#steps-to-build-dashboard)
  - [:one: Build Data Source](#one-build-data-source)
  - [:two: Build Charts](#two-build-charts)
    - [Calculated Fields Created](#calculated-fields-created)
    - [Charts Used](#charts-used)
    - [Hierarchies Created](#hierarchies-created)
  - [:three: Dashboard Build](#three-dashboard-build)
  - [Conclusion](#conclusion)
  - [What I Learned](#what-i-learned)

## Human Resources Dashboard
![HR_Dashboard](/Material/Images/HR_Dashboard.gif)
## Introduction  

In this project, I created two human resources dashboards - The Summary View and the Employee Records View
of high-level insights and the other one provides detailed employee records for in-depth analysis. 

This project is created following Baraa Salkini's course on [Udemy](https://www.udemy.com/course/the-tableau-ultimate-course-from-zero-to-hero).
## Tools I Used
**Tableau:**
**draw.io:**
**Git & Github:** My go-to for version control and tracking my project progress.

## User Story
# Steps to Build Dashboard
## :one: Build Data Source
The data for this project was provided by the course. After connecting it to Tableau, I performed an initial inspection, verifying data quality and ensuring that data types were correctly assigned to each column. The dataset was clean, and Tableau accurately mapped the data types. During this stage, I also began exploring the dataset by adding it to the worksheet for further analysis.
## :two: Build Charts
At this stage, I analyzed user requirements and identified the most suitable chart types to effectively present each requirement. I also designed a template sheet that defined the background color, font style, and custom color palette to streamline the dashboard creation process. This preparation eliminated the need for repetitive settings when starting new worksheets for the project.  

Custom Settings:
- Colors: `#03c4a1`, `#c52a87`, `#777777` and `#f5f5f5`
- Font: Trebuchet MS
- Background color: Dark  

### Calculated Fields Created
I then created several calculated fields and a test worksheet to ensure the formulas are valid.

```
Employee Location:
CASE [State]
    WHEN 'New York' THEN 'HQ
    ELSE 'Branch'
END
```
```
Total Employee Terminated:
COUNT(
    IF NOT ISNULL([Termdate])
    THEN[Employee ID]
END)
```
```
Employee Age Group:
IF [Age] < 25 THEN '<25'
ELSEIF [Age] >=25 AND [Age] < 35 THEN '25-35'
ELSEIF [Age] >=35 AND [Age] < 45 THEN '35-45'
ELSEIF [Age] >=45 AND [Age] < 55 THEN '45-55'
ELSEIF [Age] >=55 THEN '55+'
END
``` 
### Charts Used

- BAN (Big Ass Numbers) + Line Chart: Presented number of active and terminated employees
- Pie Chart:
- Heat Map:
- 

### Hierarchies Created
- Location:
- Department:


## :three: Dashboard Build
The first step at this stage was to sketch out the dashboard design briefly with draw.io . The summary view dashboard consists of three major components:  
- Navigation Bar: With logo and navigation icons
- Header: With header and filters
- Charts:  
  - Overview: Showed sum of employees, department infomration and location
  - Demographic: Revealed information on gender, education level, age and performance ratings
  - Income Analysis: Discovered correlation between education level, gender and salary

*Define different objects in sketch*  
![Dashboard1_2](/Material/Images/Dashboard1_2.png)
*Summary Dashboard sketch*  
![Dashboard1_1](/Material/Images/Dashboard1_1.png)
*Detail design for chart container* 
![Dashboard1_3](/Material/Images/Dashboard1_3.png)

With a sketch in hand, I created container structure and pulled in all elements. Then added in tooltips. I added in more calculated fields to enhance the presentation of the charts at this stage.
```
Rank Top 2 Job Counts:
RANK(
    [% Total Hired]) <= 2
)
```
```
Tenure:
IF ISNULL([Termdate])
THEN DATEDIFF ('year',[Hiredate],TODAY())
ELSE DATEDIFF ('year',[Hiredate],[Termdate])
END
```

```
Highlight Max:
WINDOW_MAX([Total Hired]) = [Total Hired]
```

## Conclusion
## What I Learned
