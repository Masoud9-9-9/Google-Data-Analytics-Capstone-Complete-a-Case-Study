#  Google Data Analytics Capstone: Complete a Case Study
Course: [Google Data Analytics Capstone: Complete a Case Study](https://www.coursera.org/learn/google-data-analytics-capstone)
## Introduction
I'm excited to guide you through the Cyclistic bike-share analysis case study. In this case study, I'll be playing the role of a junior data analyst working for a made-up company called Cyclistic. We'll meet various characters and team members and go through the data analysis process to answer important business questions. We'll follow 6 steps, [Ask]( https://github.com/Masoud9-9-9/Google-Data-Analytics-Capstone-Cyclistic-Case-Study/blob/main/README.md#ask), [Prepare]( https://github.com/Masoud9-9-9/Google-Data-Analytics-Capstone-Cyclistic-Case-Study/blob/main/README.md#prepare), [Prepare]( https://github.com/Masoud9-9-9/Google-Data-Analytics-Capstone-Cyclistic-Case-Study/blob/main/README.md#prosess), [Analyze](https://github.com/Masoud9-9-9/Google-Data-Analytics-Capstone-Cyclistic-Case-Study/blob/main/README.md#analyze-and-share), [Share]( https://github.com/Masoud9-9-9/Google-Data-Analytics-Capstone-Cyclistic-Case-Study/blob/main/README.md#analyze-and-share), and [Act](https://github.com/Masoud9-9-9/Google-Data-Analytics-Capstone-Cyclistic-Case-Study/blob/main/README.md#act),. You can rely on the Case Study Roadmap tables, which include helpful questions and tasks, to make sure we're on the right track. Let's get started!

## Scenario
I'm a junior data analyst on the marketing analyst team at Cyclistic, a bike-sharing company in Chicago. The head of marketing thinks that our company's success in the future depends on getting more people to sign up for annual memberships. So, my team wants to figure out how people who occasionally use our bikes (casual riders) are different from those who have annual memberships. We need to understand these differences to create a new marketing plan that convinces casual riders to become annual members. However, before our recommendations can be accepted, the Cyclistic executives need to see strong data insights and professional data visuals to back up our ideas.

## Characters and teams
### ● Cyclistic:
A bike-share program that features more than 5,800 bicycles and 600 docking stations. Cyclistic sets itself apart by also offering reclining bikes, hand tricycles, and cargo bikes, making bike-share more inclusive to people with disabilities and riders who can’t use a standard two-wheeled bike. The majority of riders opt for traditional bikes; about 8% of riders use the assistive options. Cyclistic users are more likely to ride for leisure, but about 30% use them to commute to work each day.

### ● Lily Moreno:
The director of marketing and your manager. Moreno is responsible for the development of campaigns and initiatives to promote the bike-share program. These may include email, social media, and other channels.

### ● Cyclistic marketing analytics team:
A team of data analysts who are responsible for collecting, analyzing, and reporting data that helps guide Cyclistic marketing strategy. You joined this team six months ago and have been busy learning about Cyclistic’s mission and business goals — as well as how you, as a junior data analyst, can help Cyclistic achieve them.

### ● Cyclistic executive team:
The notoriously detail-oriented executive team will decide whether to approve the recommended marketing program.

### About the company
In 2016, Cyclistic started a successful bike-sharing program with 5,824 bikes and 692 stations in Chicago. People can take a bike from one station and return it to any other. Their marketing used to target a broad audience with different pricing plans, including single-ride, full-day passes, and annual memberships. They found out that annual members are more profitable. Now, they want to convert casual riders into annual members to grow. The goal is to design marketing strategies by understanding the differences between these two groups and how digital media can help.

## Ask
Three questions will guide the future marketing program:

How do annual members and casual riders use Cyclistic bikes differently?
Why would casual riders buy Cyclistic annual memberships?
How can Cyclistic use digital media to influence casual riders to become members?
Moreno has assigned me the first question to answer: How do annual members and casual riders use Cyclistic bikes differently?

## Prepare
We will perform our data analysis using trip data from 2020, which has been provided by [this source](https://divvy-tripdata.s3.amazonaws.com/index.html). under their specific [license agreement](https://divvybikes.com/data-license-agreement).

## Process
### Tools
I utilize BigQuery to merge multiple datasets into a single dataset and perform data cleaning. This is necessary because Microsoft Excel can only handle up to 1 million rows and cannot effectively manage extensive datasets. Since the Cyclistic dataset contains over 3325136 rows, using a platform like BigQuery, capable of handling large data volumes, is crucial. Also, the connected sheet to BigQuery is used to drive insight from cleaned data.

### Data integrity
Data integrity is crucial to make sure that the data sample is adequate, free from any partiality, accurately mirrors the entire population, and is reliable. In this project, our data sample covers the entire population for one year, so it's unbiased, and the data comes directly from the source, ensuring accuracy and trustworthiness.

### Cleaning the data
4 CSV files named Divvy_Trips_Q1, Divvy_Trips_Q2, Divvy_Trips_Q3 and Divvy_Trips_Q4 are uploaded as tables in the dataset 'Divvy_Trips'. Then, I combined these four tables to create one table for the whole data in 2020 with the name "Divvy_Trips_2020_uncleaned", containing 3325136 rows of data. 

I will take some steps to clean the data:

1: The following image is the schema:

![image](/images/schema.png)

2. Number of __null values__ in each column is as follows:

![image](/images/null_value.png)

3. The number of duplicates in each ride_id column:

![image](/images/duplicated_row.png)

4. Rows that include null_values should be deleted.

4. Create a column called “ride_length.” Calculate the length of each ride by subtracting the
column “started_at” from the column “ended_at” (for example, =D2-C2) and format it as number of minutes.

5. Create a column called “day_of_week,” and calculate the day of the week that each ride started. Format as General or as a number with no decimals, noting that 1 = Sunday and 7 = Saturday.

6. The number of rows after cleaning data is 3325136. The new schema is as follows, 

![image](/images/new_schema.png)

## Analyze and Share
Now that the data is stored appropriately and has been prepared for analysis, I will start putting it to work. I should ask myself, how should I organize the data to perform analysis on it?

● Has the data been properly formatted?

● What surprises did you discover in the data?

● What trends or relationships did you find in the data?

● How will these insights help answer your business questions?

I will try to answer these questions by plotting different features of the data. 

First of all, I want to plot the total number of trips and average of each trips in minutes that casual and member riders used according to the type of bike.

![image](/images/Total_Trips_per_readable_type.png)

![image](/images/Average_of_ride_length_per_readable_type.png)

From the first table and chart, it is clear that about 80% of member and casual riders preferred docked bike, while small percentage of them prefer electric and classic bike. Also, we can say that both casual and member riders have similar taste in choosing different type of bikes. 
From the second plot, the most important point is that casual riders tend to ride almost twice as members. And, when it comes to docked bike type, casuals rode almost three times more than members.

Now, we are heading to compare casual and member riders trends according to month, weekday and hours  when it comes to total number of trips and average length of each trip.

![image](/images/Total_Trips_per_month.png)

![image](/images/Average_of_ride_length_per_month.png)

From the above tables, it is clear that casual riders use bike share very rare from January until April, but member users rode almost ten times more. After that, casuals demand increased steadily from May to August, in which 270 thousand bikes, we can see the similar trend in member users. So, in these months the number of trips between casual and member riders are almost similar. Then, the demand of casuals starts to decrease dramatically from September until December, however this trend for member users is gradually. 
It is noticeable that riders who are casuals rides almost rode twice more than members in each month.

![image](/images/Total_Trips_per_day_of_week.png)

![image](/images/Average_of_ride_length_per_day_of_week.png)

It is evident that casual riders used bike program in weekends twice as in the workdays. However, members rode in all days with similar pattern. Also, the duration of each trip for casuals is two times that members for each day.

![image](/images/Total_Trips_per_Hour.png)

![image](/images/Average_of_ride_length_per_hour.png)

From the above tables, trips number for casual riders start to increase gradually from 6:00 until 17:00, in which reaches the peak at 125 thousand trips, after that it starts to decrease gradually. On the other hand, for members riders, the number of trips is high at the morning from 6:00 to 8:00, and decreases a bit until 10:00, then experience a steady increase from 11:00 to 17:00. Furthermore, the length of each ride of casual riders for every hour of day is more than member users.

From all above figures, we can conclude that casual riders use bike share company most in July, August, September, and they prefer to use more bike in the weekend. So, I created a table for most frequently used station for casual riders, by filtering the months (July, August, September) and day of week (Statuary, Sunday). The result is as follows.

![image](/images/stations.png)

From the table, top 20 stations that bike share company can use to encourage casual riders to become members. Overall, the campaign should be held at the weekends of three months (July, August, September)  and at the above stations.

## Act
After identifying the differences between casual and member riders, marketing strategies to target casual riders can be developed to persuade them to become members.
Recommendations:
1.	Marketing campaigns might be conducted in July, August, September and in the weekends.
2.	They should use the most frequent stations to held their campaign.
3.	Electric bikes are less attractive for casuals and members. Offering discount might persuade both riders use them most frequent. 
