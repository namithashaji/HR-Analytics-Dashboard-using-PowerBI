# HR-Analytics-Dashboard-using-PowerBI
The Human Resource Report provides a comprehensive view of employee data across various  departments and business units. Its primary purpose is to support HR decision-making by offering  insights into workforce demographics, job classifications, job satisfaction, performance ratings, and other key metrics. This report is designed to monitor and evaluate  employee engagement, performance trends, and potential areas for improvement within the organization. The primary audience for this report includes HR managers, department heads, and executive leadership. This report aims to provide them with actionable insights for workforce planning, retention strategies, and improving overall employee satisfaction. 

## Key Objectives
Key Objectives includes tracking employee attributes like age, gender, education level, and job type to understand the organization’s demographic composition, evaluating job satisfaction, involvement, relationship satisfaction, and performance ratings to assess employee morale and effectiveness, providing insights into work-life balance indicators and sick days to help identify potential burnout or areas needing intervention, Analyzing tenure, years in current role, and years since the last promotion to gain insights into employee retention and career development within the company.

## Data Source
The dataset used is Human-Resource.csv. The dataset had a single table with 22 Columns and 3520  rows. The key data fields include Departments, Business Units, Hire date, Employee education, Job satisfaction, Salary, Age, Gender etc.

## Data Transformation (Power Query)
Data cleaning and transformation steps:
- Promoted headers: At the beginning the headers were not set. The headers were occupied in first row. So, to promote headers from row 1 we used “Use First Row as Headers” option under Transform tab. 
- Split Column by Delimiter: The Hire Date was in MM/DD/YYYY format. To separate them into 3 different columns “Split column” is used by right clicking on column header. 
- Reordered Columns: The columns were reordered such that it is ordered as DD MM YYYY. 
- Merged Columns: Date column, Month column and Year column were merged together and named “Date” 
- A new column “ID” is created combining Last name and Salary. This is done by selecting both columns clicking ctrl key and then right click -> Add Columns from Examples -> Type the way we need the id look like (eg: horn89900) and hit Enter.
-  Replaced values in “Years in current role” and “Years since last promotion”  so as to convert it to number format. 
- Converted “Performance Rating” to a range of 1 to 4
- Changed Type: This done by clicking ctrl+A to select whole data -> Transform tab -> Detect data type

## DAX Measures
DAX is a formula language used in Power BI to perform data manipulation and analysis. It allows users to create powerful data insights and perform complex calculations, such as aggregations, time-based analysis, and conditional logic. There were mainly ten Dax measures created from Human Resource table namely: 
- Total Active Employees = CALCULATE([Total Employees],'Human 
- Resources'[Emp.Type]="Active") 
- Total Balance Days = SUM('Human-Resources'[Balance Days]) 
- Total Employees = COUNTROWS('Human-Resources') 
- Total Salary Cost = SUM('Human-Resources' [Salary]) 
- Total Sick Days = SUM('Human-Resources' [Sick Days]) 

## Data Visualizations
![Dashboard Overview](images/Dashboard.png)
This human Resource Dashboard provides a structured and interactive visualization of key HR metrics. This helps the stakeholders analyze workforce performance, engagement, and demographics effectively.  The visualizations includes Cards which shows Total Work days, Total salary, Total Employees and Total active employees, a gauge chart which shows the average performance rating of employees. Then we have a bar chart showing Total Salary and Sick Days by Department, Clustered Column Chart that gives Average of Years Since Last Promotion by Job Involvement and Education and so on as given in the screenshot. Interactive features are given to the dashboard by including slicers such as year, department, business unit etc. and a gender toggle button.

## Data Insights
**By analyzing the overall data from 2013 to 2018, it can be seen that:**
- As the Salary increases, the no. of Sick days also increases within departments. 
- Employees with higher average Sick days tend to have the best worklife balance. 
- As age increases the Employee Job satisfaction drops when there is no increment in salary. 
- Younger employees tend show very high job satisfaction even if the least salary is offered.

**Job satisfaction v/s Average performance rate**
![Average performance rate](images/performance-rate.png)
- From the above screenshot we can see that as job satisfaction increases average performance rate also increases.

SUGGESTION: Increasing salary of elder employees will increase the performance rating.

**Job Involvement v/s Promotion**
![Promotion](images/job-involvement.png)
- Considering an average elder employee with a doctorate degree, It tend to have a frequent promotion for those who has higher job involvement than an average younger employee. 
- While an average younger employee with a bachelors degree tend to get a frequent promotion when he possess a medium job involvement.

SUGGESTION: Hiring more freshers is profitable to the company since they show higher job satisfaction with the least salary hike and possess a medium level of job involvement.

## Comparing 2013 Data insights and 2018 Data Insights
- The Total Salary spend on Employees has increased from $52.93M to $59.12M. (11.69% increase) 
- Average performance rating increased from 2.47 to 2.53 
- In 2013, Human Resource was the department getting highest total salary($4.87M) with 52 employees. 
- In 2018, Advertising became the most paid department($4.81M) with 51 employees.  
- In 2013, younger employees were paid the least salary. In contrast the highest paid in 2018 were the youngest employees. 
- Group B had the most hirings in 2013. In contrast it was the least hired group in 2018.

OBSERVATION: From comparing 2013 Human Resource data and 2018 data, we can see that  
younger employees are hired more than elder employees and more salary is invested in advertising 
department.
