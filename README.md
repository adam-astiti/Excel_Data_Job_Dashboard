# 📊 Interactive Data Job Vacancy Dashboard

![image](https://github.com/user-attachments/assets/b75ce3d1-684e-422c-9cb5-aa3be3d211e7)
image description: A snapshot of the main dashboard, showcasing key metrics and interactive filters.

## 📌 Project Overview
As an aspiring Data Analyst navigating the current job market, I developed this interactive dashboard to gain a comprehensive understanding of the global landscape for data-related roles in 2023. The goal of this project was to move beyond simple job listings and create a centralized tool that answers critical questions for any data professional in training or on the job hunt.

This dashboard is designed to help users, especially aspiring analysts and job seekers, to:

- Identify the most **in-demand job roles** within the data industry.
- Understand **salary expectations** and benchmarks for various positions.
- Discover which **countries** have the highest demand for data professionals.
- Recognize the **most popular platforms** for finding data-related job opportunities.
- Gauge the **key skills** required for different roles, particularly for data and business analysts.
  
## 💡 Key Insights
From the 26,712 job vacancies analyzed, several key trends emerged:

- **High Demand, Lower Salary for Data Analysts**: The Data Analyst role shows the highest demand across the globe. However, it also has the lowest median salary among the technical data roles analyzed, suggesting it's a common entry point into the field.

- **Top Skills for Analysts**: For Data and Business Analyst roles, a core set of skills is consistently in demand: SQL, Excel, Python, and Tableau. This highlights the foundational tools required to enter the industry.

- **Leading Job Platform**: Ai-Jobs.net emerged as the most-used platform for posting data jobs, surpassing larger, more generalist platforms like LinkedIn.

- **USA Leads the Market**: The United States has the highest number of job postings, indicating it is the largest and most active market for data professionals.

- **Specialized Roles Command Higher Salaries**: While demand is highest for general analyst roles, more specialized positions like Senior Data Scientist ($150K) and Senior Data Engineer ($148K) command significantly higher median salaries.

## 🛠️ Tools & Technologies Used
This dashboard was built entirely within Microsoft Excel, leveraging its advanced data capabilities to perform tasks from data cleaning to interactive visualization.

![image](https://github.com/user-attachments/assets/5292d7cd-8852-494a-8f49-0fcdd2da37d2)
image description: dirty raw data in power query

**1. Data Cleaning and Transformation (Power Query)**
The initial dataset was processed using Power Query for a robust and repeatable ETL (Extract, Transform, Load) pipeline.
- **Column Selection**: Irrelevant columns were removed to optimize the dataset.
- **Data Type Correction**: Ensured each column had the correct data type (e.g., Text, Fixed Decimal Number) and handled resulting errors by converting them to nulls.

![image](https://github.com/user-attachments/assets/86f3fdcc-cefd-496a-93ff-222d386438bb)

image descripton: Data Model

- **Data Modeling (Star Schema)**:
To analyze the unstructured job_skills column, I modeled the data into a Star Schema.
- The skills data was split and unpivoted so that each skill for a job had its own row. This created a **Skills Dimension Table** linked to the main Fact Table via the job_id, forming a clean one-to-many relationship.
- **Feature Engineering (M Language)**:
A single, unified salary column was engineered from the salary_year_avg and salary_hour_avg columns using a Custom Column with M Language. The logic applied was: if [salary_year_avg] is null then [salary_hour_avg] * 2080 else [salary_year_avg].
- **Outlier Detection**: Outliers in the salary column were identified and flagged using the Interquartile Range (IQR) method. These were not deleted but were excluded from certain calculations in Power Pivot to ensure analytical accuracy.

![image](https://github.com/user-attachments/assets/3cfe8a56-9024-44a1-9b5b-dae174c4ad0c)
image description: Pivot chart fields with measures

**2. Data Analysis and Calculation (Power Pivot & DAX)**
- **PivotTables**: Used for straightforward aggregations and as the foundation for most charts.
- **Power Pivot & DAX**: For calculations too complex for standard PivotTables, I used Power Pivot's data model. DAX (Data Analysis Expressions) measures were written to accurately calculate the Median Salary and the average number of skills required per job title.
  
![excel project](https://github.com/user-attachments/assets/0494e04c-a996-4f8e-a10a-e2e339d06d4a)
image description: Interactive slicer and link

**3. Visualization and Dashboard Design**
- **Pivot Charts & Standard Charts**: A combination of Pivot Charts for dynamic reporting and standard Excel charts (like Scatter Plots)
- linked to **PivotTable** data was used for a wider range of visualizations.
- **Slicers**: Interactive Slicers for Country and Job Type were implemented to allow users to easily filter the entire dashboard.
- **UI/UX Design**: A deliberate color palette was chosen using a color wheel to ensure the dashboard is not only functional but also visually appealing and easy to read. Navigation buttons are used to switch between different views or pages.
