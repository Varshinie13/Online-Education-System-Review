# Online-Education-System-Review
This project explores the intersection of digital infrastructure, socio-economic status, and student performance during the shift to online education. By analysing a dataset of 1,033 students, the project identifies key barriers to learning such as the "Digital Divide"and highlights behavioural patterns that lead to academic success or distraction.

Data Sources
•	Primary Dataset: Online_Education_Trends_2021_1
•	Size: 1,033 Rows.
•	Origin: https://data.mendeley.com/datasets/bzk9zbyvv7/1/files/e4c6c2bd-eb9a-40ac-8642-d1796871dedb

Problem Statement

The rapid transition to online learning has not been equitable. Students face varying challenges based on their geographical location, family size, and economic standing. This project aims to answer:

1.	How does economic status impact access to quality learning tools?
2.	Which level of education spends the most time on social media?
3.	Which student segments are at the highest risk of "Distraction"?
4.	Does most of the student population have internet facilities in their local area?
5.	What age of Students spends the most time on social media?
6.	Is there a correlation between a student's economic status and the amount of time they dedicate to studying?
7.	Does having an elderly family member monitoring a student actually increase their study time?
8.	Is there a Study Intensity Correlates with Social Media Time?
9.	Do most students prefer a practical, theoretical, or balanced approach to learning?
10.	Are rural students more satisfied with their learning environment than urban students?

 Tools & Technologies
•	Microsoft Excel: Initial data cleaning and structure validation.
•	Power Query: Data transformation, handling null values, and formatting columns.
•	Power BI Desktop: DAX implementation, Data modeling, and Interactive visualization.
•	Canva: Used for designing the background layout of the dashboard.

 Data pre-processing
•	Cleaning: Standardized categorical values to ensure consistency in charts.
•	Transformation: Used Power Query to create conditional columns for "Performance Rank" and "Study Intensity."
•	Normalization: Ensured numerical columns like "Average Score" and "Sleep Time" were correctly typed for aggregation.


DAX (Data Analysis Expressions)
Key measures and columns were authored to drive the logic of the dashboard:
•	Level of Subjects = IF(Online_Education_Trends_2021_1[Number of Subjects] > 6,"MaximumSubjects","Minimum Subjects")

•	Study Intensity = SWITCH(TRUE(),
'Online_Education_Trends_2021_1'[Study time (Hours)] >= 6, "High Intensity",
'Online_Education_Trends_2021_1'[Study time (Hours)] >= 3, "Moderate     Intensity", "Low Intensity")

•	Performance Variance = [Performance in online] - CALCULATE(AVERAGE('Online_Education_Trends_2021_1'[Study time (Hours)]), ALL('Online_Education_Trends_2021_1'))

•	Ideal Study Environment = IF('Online_Education_Trends_2021_1'[Internet facility in your locality] >3  && 'Online_Education_Trends_2021_1'[Have separate room for studying?] = "Yes", "Yes", "No")

Measures: 

•	Total Students = COUNTROWS('Online_Education_Trends_2021_1')

•	Digital Access % = DIVIDE(CALCULATE([Total Students], 'Online_Education_Trends_2021_1'[Internet facility in your locality] > 3 && 'Online_Education_Trends_2021_1'[Have separate room for studying?] = "Yes"), [Total Students], 0)

•	Satisfaction % = DIVIDE(CALCULATE([Total Students], 'Online_Education_Trends_2021_1'[Level of Satisfaction] = "Good"), [Total Students], 0)

•	Group Study % = DIVIDE(CALCULATE([Total Students], 'Online_Education_Trends_2021_1'[Engaged in group studies?] = "Yes"), [Total Students])

Analysis & Visualization

The dashboard is divided into two primary analytical views:
Page 1: Digital Divide
•	Treemap: Visualizes the distribution of devices (Laptop vs. Mobile).
•	Donut Chart: Shows "Distraction Risk" weighted by economic status.
•	Line and Clustered Column Chart: Compares Social Media time and Study time by age.
•	Funnel Chart : Compares Time spent on Social media by Level of Education.
•	Decomposition Tree : It identifies the hidden root causes of student performance.
•	Clustered Column Chart: Separate room vs Family Size.

Page 2: Habits & Lifestyle
•	100% Stacked Bar Chart: Correlation between Clearing Doubts and Group Study engagement vs Level of Education.
•	Line Chart: Social Media Time and Study Intensity Vs Level of Education.
•	Stacked Bar Chart: Family Size Vs Separate room for Studying.
•	Tree Map: Home Location Vs Level of Satisfaction.
•	Ribbon Chart: Study Time by Age Vs Elderly Monitored Students.
•	Line and Stacked Column Chart: Average Score Vs Sleep Time by Level of Education.
•	Funnel Chart: Mode of Interest by Total Students.
•	Clustered Column Chart: Study Time by Economic Status.
•	Slicers: Allow users to filter the entire report by "Level of Education" and "Study Intensity.

Dashboards:

<img width="960" height="540" alt="Screenshot 2026-04-08 204558" src="https://github.com/user-attachments/assets/92304667-f8a6-417d-ad73-89037308e85f" />
<img width="960" height="540" alt="Screenshot 2026-04-08 204337" src="https://github.com/user-attachments/assets/d0d3d009-87ff-4588-aef1-290f8f2f41ff" />



Insights & Conclusions

Descriptive Analysis

•	Most of the student population belongs to the "Middle Class" and resides in "Urban" areas.
•	Laptop usage is the dominant mode of learning, but a significant portion still relies on mobile devices. While Laptops are the primary tool, a massive segment of 334 students (approx. 33%) attend classes via Mobile, which correlates with lower "Performance Ranks" in complex subjects.
•	Urban students have a 54.79% better access to internet facilities compared to Rural students. This confirms a geographical "Digital Divide.
•	The dataset shows a balanced Gender distribution, but "Level of Satisfaction" varies, with Urban females reporting higher satisfaction than Rural females due to better "Internet Locality.

Diagnostic Analysis

•	Lower academic scores in "Rural" areas are directly linked to poor "Internet Facility" and the lack of a "Separate Room for Studying. The "Separate Room for Studying" column is a major driver of success. Students with a private space show a 15% higher Average Score than those in large "Family Sizes" (6+ members) without a dedicated room.
•	The "Distraction Risk" is highest in the "Middle Class." Diagnosis shows this is due to high "Time Spent on Social Media" (avg 3+ hours) paired with "Mobile" device usage, which facilitates easier switching between study apps and entertainment.
•	Students where "Elderly people monitor you" show a consistent study intensity, whereas unmonitored students have a higher "Performance Variance."

Predictive Analysis

•	Students spending >4 hours on social media with <2 hours of study time are 85\% more likely to fall into the "Distracted Learner" profile.
•	Based on the "Sleep Time" vs. "Average Score" trend, students who sleep less than 5 hours are predicted to see a 12% drop in "Performance Rank" over the next semester due to "Study Intensity" fatigue.
•	Students who select "No" for both "Interested in" and "Engaged in group studies" are at a high risk of dropping out or reporting "Bad" satisfaction levels in online modes.

Prescriptive Analysis

•	Recommendation: To improve "Rural" performance, educational institutions should provide offline learning modules to mitigate poor internet access. Encouraging "Group Studies" is shown to increase satisfaction levels significantly.
•	Since "Internet Facility" is the bottleneck, schools should prescribe asynchronous learning (recorded videos) rather than live "Online Mode" interactions to ensure those with poor connectivity aren't left behind.
•	Students identified as "Distracted Learners" should be prescribed "Group Study" sessions. The data shows that "Clearing Doubts with Faculties" is 20% more effective when students participate in peer groups.
•	To reach an "Ideal Study Environment," the data suggests a combination of a "Separate Room" and "Laptop" usage. Even in "Poor" economic statuses, providing a quiet space (Separate Room) significantly mitigates the negative impact of low income.

Conclusion

The project demonstrates that academic success in online education is not solely dependent on a student's intelligence but heavily influenced by their socio-economic infrastructure. By addressing the Digital Divide and Personal Habits.
The "Digital Divide" is real—Home Location and Economic Status set the baseline for a student's potential. However, behavioural attributes like Study Intensity, Group Study engagement, and Sleep Management act as powerful "equalizers." If a student from a "Poor" background maintains high study intensity and utilizes group studies, they can bridge the performance gap caused by their economic status.
Ultimately, for online education to be effective, stakeholders must move beyond just providing internet; they must foster an "Ideal Study Environment" that minimizes "Distraction Risk" and maximizes "Student Profile" focus.


