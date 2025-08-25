# Employee-Performance-power-bi-Report
![Dash1](Employee%20powerbi%201.png)
![Dash2](Employee%20power%20bi%202.png)
![Dash3](Employee%20powerbi%203.png)
![Dash4](Employee%20powerbi%204.png)


🚀 Interactive Power BI Dashboard using DAX Designed a raw layout and implemented advanced DAX measures to create dynamic visuals. 
Used calculated columns, measures, and filters to analyze key performance metrics. Built slicer-based navigation and applied conditional formatting for better insights.
Employee Training & Performance Analysis Dashboard

#  📌 Project Overview

This project focuses on analyzing employee training, performance, and attrition data using Power BI. The goal was to build an interactive dashboard that enables HR teams and managers to monitor employee performance, track training effectiveness, and identify top-performing employees and trainers.
The dataset used was Messy HR Data, which required data cleaning, transformations, and DAX calculations to create meaningful insights. Key measures such as average training cost, employee satisfaction score, engagement score, attrition rate, and training outcomes were calculated to provide a holistic view of workforce performance.



# 🎯 Objectives

- Identify top-performing employees based on rating, engagement, work-life balance, and active employment status.

- Highlight top 10 trainers by tenure, training duration, and cost efficiency.

- Track training programs conducted and their outcomes (Completed, Passed, Failed, Incomplete).

- Monitor employee attrition trends by department, category, termination type, and gender.

- Analyze satisfaction, work-life balance, and engagement scores in relation to training duration and costs.

- Provide HR managers with interactive filters (by year, department, business unit, etc.) for deep insights.




# 🛠️ Approach & Methods

Data Cleaning & Transformation: Removed inconsistencies and standardized HR data.

# DAX Calculations:

# Top Employees:
```Dax
top1 = 
SELECTCOLUMNS(
    TOPN(10, 
        FILTER('Messy_HR_Dataset_Detailed',
            [Current Employee Rating] > 4 &&
            [Engagement Score] > 4 &&
            [EmployeeStatus] IN {"Active","Future Start","Leave of Absence"} &&
            [Work-Life Balance Score] > 4
        ), [Current Employee Rating], DESC
    ),
    "Employee Name", [Employee Name],
    "Employee ID", [Employee ID],
    "Employee Rating", [Current Employee Rating],
    "Training Outcome", [Training Outcome]
)
```
# Top Trainers:
```Dax
TopTrainers =
SELECTCOLUMNS(
    TOPN(10,
        FILTER('Messy_HR_Dataset_Detailed',
            [Tenure-Days] > 5 &&
            [AverageTrainingCost] <= 200 &&
            [Training Duration(Days)] > 4
        ),
        [Training Duration(Days)], DESC,
        [AverageTrainingCost], DESC
    ),
    "Name", [Trainer],
    "Tenure", [Tenure-Days],
    "Training Cost", [Training Cost],
    "Gender", [GenderCode],
    "Department", [DepartmentType],
    "Job", [JobFunctionDescription]
)
```

## Visualizations Created:

- Training programs vs. outcomes

- Employee attrition trends (monthly, by department & termination type)

- Employee satisfaction vs. training duration

- Top employees and trainers card visuals with photos

- Attrition and performance drill-down reports
