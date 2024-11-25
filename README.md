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

In this project, I developed two human resources dashboards: Overview and Employee Details. These concise and interactive dashboards effectively present key insights into employee demographics, departmental distribution, income levels, and educational backgrounds.

This project is created following Baraa Salkini's course on [Udemy](https://www.udemy.com/course/the-tableau-ultimate-course-from-zero-to-hero). Dataset used in this course was generated by ChatGPT and Faker library.  

Check out my HR dashboard on [Tableau Public](https://public.tableau.com/app/profile/mei.liu4813/viz/HumanResourcesDashboard_17325382179870/DetailDashboard).

## Tools Used
**:art: Tableau:** A powerful data visualization and business intelligence tool. It enables users to analyze, visualize, and share insights through interactive dashboards and reports.
*:pencil2: *draw.io:** A versatile, web-based diagramming tool. I used draw.io to sketch container structure.
**:octopus:Git & Github:** My go-to for version control and tracking my project progress.

# Steps to Build Dashboards
## :one: Define User Requirements
## :two: Build Data Source
The data for this project was provided by the course. After connecting it to Tableau, I performed an initial inspection, verifying data quality and ensuring that data types were correctly assigned to each column. The dataset was clean, and Tableau accurately mapped the data types. During this stage, I also began exploring the dataset by adding it to the worksheet for further analysis.
## :three: Build Charts
At this stage, I analyzed user requirements and identified the most suitable chart types to effectively present each requirement. I also designed a template sheet that defined the background color, font style, and custom color palette to streamline the dashboard creation process. This preparation eliminated the need for repetitive settings when starting new worksheets for the project.  

Custom Settings:
- Colors: `#03c4a1`, `#c52a87`, `#777777` and `#f5f5f5`
- Font: Trebuchet MS
- Background color: Dark  

**Calculated Fields Created**
I then created several calculated fields and tested to ensure all formulas are valid.

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
Age:
DATEDIFF('year',[Birthdate],TODAY())
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
```
Highlight Max:
WINDOW_MAX([Total Hired]) = [Total Hired]
```
```
Hightlight Max Percentage:
WINDOW_MAX([% Total hired]) = [% Total hired] 
```
```
Highlight Top 2 Job Titles:
RANK([% Total Hired]) <= 2
```


**Charts Used**

- **:chart_with_upwards_trend: BAN (Big Ass Numbers) + Line Chart:** Ideal for presenting KPIs at a glance. I combined BANs with line charts to show the trend of active and terminated employees over time.  
![BAN](/Material/Images/BANs.png)  
- **:bar_chart: Bar Chart:** Effective for visualizing distributions. In this dashboard, bar charts were used to display the distribution of employees across departments. They also provided breakdowns of dimensions like education levels and age groups.  
![Bar_Chart](/Material/Images/Bar_Chart_Department.png)  
- **:globe_with_meridians: Map**: Used to illustrate location hierarchies, detailing relationships between location, state, and city.  
![Map](/Material/Images/Map_Location.png)  
- **:pizza: Pie Chart:** Represented gender distribution and the proportion of active versus terminated employees in a visually intuitive format.  
![Pie_Chart](/Material/Images/Pie_Gender.png)  
- **:fire: Heat Map:** Highlighted relationships and distributions between dimensions. Two heat maps were created: Age Group vs. Education Level and Education Level vs. Performance Rating. The highest percentages and counts were visually emphasized.  
*Age Group vs. Education Level*  
![Heat_Map_1](/Material/Images/Heat_Map_1.png)    
*Education Level vs. Performance Rating*  
![Heat_Map_2](/Material/Images/Heat_Map_2.png)  
- **:red_circle::heavy_minus_sign::white_circle: Barbell Chart:** Revealed the gender pay gap across different education levels, providing a clear view of disparities.  
![Barbell_Chart](/Material/Images/Barbell_Chart.png)  
- **:milky_way: Scatter Plot:** Demonstrated the relationship between age and salary, uncovering potential trends and correlations.  
![Scatter_Plot](/Material/Images/Scatter_Plot.png)  
## :four: Dashboard Build
The first step at this stage was to sketch out the dashboard design briefly with draw.io.
The sctrucre for the **Overview Dashboard** is:  
- Navigation Bar: With logo and navigation icons
- Header: With header and filters
- Charts:  
  - Overview: Showed sum of employees, department infomration and location
  - Demographic: Revealed information on gender, education level, age and performance ratings
  - Income Analysis: Discovered correlation between education level, gender and salary

*Define different objects in the sketch*  
![Dashboard1_2](/Material/Images/Dashboard1_2.png)  
*Overview Dashboard sketch*   
![Dashboard1_1](/Material/Images/Dashboard1_1.png)  
*Detail design for chart containers*   
![Dashboard1_3](/Material/Images/Dashboard1_3.png)  

The sctructure for the **Employees Details Dashboard** was very similar to the Overview Dashboard:
- Navigation Bar: With logo and navigation icons
- Header: With header. Filter removed from this section
- Filters container: Total of seven filters containers on top of the detail list
- Employees details list  

*Detail list Dashboard sketch*  
![Employee_details_sketch](/Material/Images/Employees_Details_Sketch.png)  
*Filter design*  
![Filter_desgin](/Material/Images/Filter_Design.png)  

With a sketch in hand, I created container structure and pulled in all elements. Then added in dynamic tooltips. I added in more calculated fields to enhance the presentation of the charts at this stage.




## Conclusion
## What I Learned
