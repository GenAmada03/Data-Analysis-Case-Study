# Case Study 1: Bellabeat analysis
### Introduction

Bellabeat manufactures smart devices designed to improve the health and well-being of women. Since 2013, Urška Sršen and Sando Mur, co-founders, have been instrumental in its explosive growth. The artist Sršen created technology that enables women to monitor important health indicators, such as stress, sleep, activity, and reproductive health. Bellabeat has established itself as a progressive, technologically advanced business in the women's wellness sector.

Scenario
I am tasked by the Chief Creative Officer of the Bellabeat company to identify and analyze smart device usage trends that can help them develop their marketing strategy. I will take the role of a data analyst in this scenario and understand how users engage with their product and derive insights to be presented to the Bellabeat’s executives which will potentially leverage the success of the business.

### Ask

- Business Task: Identify trends in smart device usage that can inform a more effective marketing strategy.
- Key Stakeholders:
Urška Sršen — Bellabeat’s cofounder and Chief Creative Officer
Sando Mur — Mathematician and Bellabeat’s cofounder; key member of the Bellabeat executive team
Bellabeat marketing analytics team — A team of data analysts responsible for collecting, analyzing, and reporting data that helps guide Bellabeat’s marketing strategy.
- Key Questions to Analyze:
  - What trends can be observed in smart device usage?
  - How can these trends be applied to Bellabeat customers?
  - How can these trends shape Bellabeat’s marketing strategy?

### Prepare 
#### Tools Used in Analysis
1. Data Cleaning: Microsoft Excel and Big Query
2. Data Analysis: Big Query 
3. Visualizations: Excel and Tableau

#### Data Source
The primary dataset used for the analysis was downloaded from Kaggle and a data dictionary was used to guide the meaning of values.  
Unzip the downloaded files in a folder and organize them with following by file naming.
I explored the files initially using Microsoft Excel to view the schema, check data types, number of records, validate values and more. 
- Files source: [FitBit Fitness Tracker Data](https://www.kaggle.com/datasets/arashnic/fitbit?select=mturkfitbit_export_4.12.16-5.12.16), [Data Dictionary](https://www.fitabase.com/media/1930/fitabasedatadictionary102320.pdf)


### Process
#### Data Cleaning
The SQL files were explored through:
  - checking distinct values
  - making counts
  - joining fields together
1. Data was initially loaded to excel to pre-format table date fields to match the SQL BigQuery default data type. Datasets were uploaded then to BigQuery and assigned table names.
2. Check how many unique users through ID. There are inconsistent set of users recorded in the data tables in a dateset. Upon further checking, the data are also inconsistent for daily activity table, with some values are logged while some are missing. 
4. Resort to narrowing down the sample size of users which have consistent numbers of logged days in the daily activity table. The users were limited to those who logged for April 12 - May 12, 2016 only. Out of 33 users, it was identified that 24 users have 30 complete records for each day from the mentioned date range. The daily activity table shows lots of relevant information since it has the summary in a day of values like daily active minutes spent by the user and activity intensity.
5. Weight Log Info table shares users demographics and was inspected. 8 unique users are present and there was no missing values apart from the fat field.

### Analyze
**Finding out the user demographics.**
   Through the Weigh Log Info data, the background of users will be revealed. One of the information included in the table is Body Mass Index (BMI). It is widely used as a general indicator of whether a person has a healthy body weight for their height. In order to see the status of the current user population of the smart device, their BMI was averaged. The analysis was limited to only 8 users because of the data availability. Specifically, the value obtained from the calculation of BMI is used to categorize whether a person is underweight, normal weight, overweight, or obese depending on what range the value falls between. 
   
   <p align=center><img src="https://github.com/user-attachments/assets/9197cb48-3337-407b-8aba-efc842c33aca" alt="TotalUsersAvgBMI" width="600" height="340">

  It shows that majority of the users are normal in weight, and ther is no underweight users. This shows the potential market to target next time. The company could give more encouragement to people at extreme categories who might use less of smart device and have the company tailor their smart device products according to the needs of these people. 

**Intensity and Sleep.**
A lot of research that have examined the relationship between exercise and sleep have found that some forms of physical activity enhance the length and quality of sleep. 
It was found out that intensity of the activity impacts sleep quality. The exercise was associated with improved sleep quality but there was this case of negative association with high-intense physical activity and sleep quality. https://pmc.ncbi.nlm.nih.gov/articles/PMC10503965/#REF3 

<p align=center><img src="https://github.com/user-attachments/assets/1c4cd8da-15fc-44e0-becb-150f094a81db" alt="IntensityVsTime" width="700" >

The data from Hourly Intensity table was helpful to review users when is the most intense activity done within a day. Each users have values of their activity intensity per hour and they were averaged and contrasted to military time. It shows users exert more active intensity between 5 and 23. This activity tends to peak around 17and 19, and we may assume this was due to users getting off from work.

<p align=center><img width="700" alt="time_asleep_table" src="https://github.com/user-attachments/assets/63dd0754-4e3c-4eab-b20c-41fe0a2fc9d7">
  
On the other hand, the total of hours users asleep distribution is presented. We can see most of users length of sleep in hours and they mostly have almost 6 hours of sleep to a little beyond 9. However, this data can only be a guide since the total time asleep might come from sum of full bedtime sleep and naps from any point of a day. According to a [website](https://www.sleepfoundation.org/how-sleep-works/how-much-sleep-do-we-really-need), adults are recommended to have 7 hours or more of sleep atleast for adults. For the population of users of the bellabeat, it is important to have activities with certain intensities done earlier periods of the day if they have the users wish to follow on time and quality sleep. It is nice to add a feature in its application suggestions of kind of activity to do especially in the peak time of 17:00 onwards.

**Activeness of Users.**
According to [CDC](https://www.cdc.gov/physical-activity-basics/guidelines/adults.html#:~:text=Physical%20activity%20is%20one%20of,muscle%2Dstrengthening%20activity%20each%20week), adults need 150 minutes of moderate-intensity physical activity a week. This can also be 75 minutes of vigorous-intensity or an equivalent combination of moderate- and vigorous-intensity physical activity. In addition, adults need at least 2 days of muscle-strengthening activity each week. 
<p align=center><img src="https://github.com/user-attachments/assets/a9599e96-5418-4898-8b94-b0ca361b2584" alt="ActiveMinsDstrb" width="600">

  From the graph above, we can see the users spent their time active in a day. The data from 33 unique users were averaged and compared to see the fraction of each in all categories of active minutes (very, lightly, fairly, and sedentary). In the pie chart just right above, we can see the sedentary minutes have the highest percentage with 86% while fairly and very active minutes in a day are only aprroximately 1%. Within a day, sleeping takes a lot of our time but it is also a sedentary activity. Taking it into account, we can see how much is what's left in sedentary minutes excluding the time the users were asleep.
  
<p align=center><img  src="https://github.com/user-attachments/assets/f0c374e3-8821-411f-a428-8a4d3f97ad20" alt="ActivenessAndTotalSleep" width="550">

The chart shows 34% of the time is taken in the day on average from the users when they were asleep. That leaves 56% of sedentary active minutes which is same by saying users on average spent approximately 13 hours sedentary in a day, which is long. It can be thought of sedentary active minutes are spent from prolonged time watching or playing video games, but it is possible that they come from user's nature of job such as office-based work and driving. So depending on the users goal, the smart device could incorporate engaging features and send information to push users achieve their goal such as notifications or challenges in the application like a fun activity game. The users can also have the chance to check out some peers that use smart devices so they'll be more motivated and learn in the environment where everyone cares for their health.

### Recommendations

Bellabeat's mission is to empower women with data about their own health and behaviors. They accomplish this by tracking data on activity, sleep, stress, and reproductive health. They have succeeded in this mission and established themselves as a tech-driven health firm for women since its foundation in 2014. Though provided Fitbit fitness tracker data have incomplete and few useable data for particular fitness aspect, I was able to discover insights that can reveal more opportunities for growth and improve the Bellabeat marketing strategy.

#### Recommendations
1. Amplify marketing of the product to a certain category of users in BMI. The category of users for BMI  with least users are in the extreme categories of BMI (underweight and obese).
2. Promote relaxation before sleep. Add calming feature like pulling a playlist of soothing music or add night feature for the app. The application can suggest activities with certain intensities appropriate for the time of the day tailor fit to the user's goal of on time and quality sleep. 
3. Bellabeat devices are connected with a mobile application. The app can improve to personalize its feature if users can have goals to target like adding a fun game. Give the users a choice to receive notification  of reminder to start their goals and alert when it is going sideways. The application can also  suggest activities of certain intensities or be linked to other fitness apps that encourage people to get off their feet like following an exercise. Have challenges that create friendly competition, while rewards like virtual badges, product discounts, or exclusive content can serve as motivation to stay active and engaged with the app.
4. It is proposed to add a community talk among users online. A forum social network where users can share their analytics, and exchange thoughts to communities of smart device users where they dive into their interests, hobbies, and passion towards a fit and healthy versions of themselves.

 Thank you for taking the time to read through this analysis. The SQL analysis and additional excel works are uploaded in a folder together with this file in Github as support documents.
