#  Google Data Analytics Capstone: Complete a Case Study
Course: [Google Data Analytics Capstone: Complete a Case Study](https://www.coursera.org/learn/google-data-analytics-capstone)
## Introduction
I'm excited to guide you through the Cyclistic bike-share analysis case study. In this case study, I'll be playing the role of a junior data analyst working for a made-up company called Cyclistic. We'll meet various characters and team members and go through the data analysis process to answer important business questions. We'll follow 6 steps, [Ask]( https://github.com/Masoud9-9-9/Google-Data-Analytics-Capstone-Complete-a-Case-Study/blob/main/README.md#ask), [Prepare]( https://github.com/Masoud9-9-9/Google-Data-Analytics-Capstone-Complete-a-Case-Study/blob/main/README.md#prepare), [Process]( https://github.com/Masoud9-9-9/Google-Data-Analytics-Capstone-Complete-a-Case-Study/blob/main/README.md#prosess), [Analyze](https://github.com/Masoud9-9-9/Google-Data-Analytics-Capstone-Complete-a-Case-Study/blob/main/README.md#analyze-and-share), [Share]( https://github.com/Masoud9-9-9/Google-Data-Analytics-Capstone-Complete-a-Case-Study/blob/main/README.md#analyze-and-share), and [Act](https://github.com/Masoud9-9-9/Google-Data-Analytics-Capstone-Complete-a-Case-Study/blob/main/README.md#act),. You can rely on the Case Study Roadmap tables, which include helpful questions and tasks, to make sure we're on the right track. Let's get started!

## Scenario
I'm a junior data analyst on the marketing analyst team at Cyclistic, a bike-sharing company in Chicago. The head of marketing thinks that our company's success in the future depends on getting more people to sign up for annual memberships. So, my team wants to figure out how people who occasionally use our bikes (casual riders) are different from those who have annual memberships. We need to understand these differences to create a new marketing plan that convinces casual riders to become annual members. However, before our recommendations can be accepted, the Cyclistic executives need to see strong data insights and professional data visuals to back up our ideas.

## Characters and teams
### ● Cyclistic:
A bike-share program that features more than 5,800 bicycles and 600 docking stations. Cyclistic sets itself apart by also offering reclining bikes, hand tricycles, and cargo bikes, making bike-share more inclusive to people with disabilities and riders who can’t use a standard two-wheeled bike. The majority of riders opt for traditional bikes; about 8% of riders use the assistive options. Cyclistic users are more likely to ride for leisure, but about 30% use them to commute to work each day.

### ● Lily Moreno:
The director of marketing and my manager. Moreno is responsible for the development of campaigns and initiatives to promote the bike-share program. These may include email, social media, and other channels.

### ● Cyclistic marketing analytics team:
A team of data analysts who are responsible for collecting, analyzing, and reporting data that helps guide Cyclistic marketing strategy. 

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
To streamline the process of merging multiple datasets and ensure effective data cleaning, I leverage BigQuery instead of Microsoft Excel. The decision is based on the limitation of Excel, which can handle only up to 1 million rows and is not equipped to efficiently manage extensive datasets. Given that the Cyclistic dataset boasts over 3541683 rows, the use of BigQuery becomes essential for handling such large data volumes. Additionally, the connected sheet to BigQuery plays a pivotal role in deriving insights from the cleaned data.

### Data integrity
Data integrity is crucial to make sure that the data sample is adequate, free from any partiality, accurately mirrors the entire population, and is reliable. In this project, our data sample covers the entire population for one year, so it's unbiased, and the data comes directly from the source, ensuring accuracy and trustworthiness.

### Cleaning the data

Four CSV files, Divvy_Trips_Q1, Divvy_Trips_Q2, Divvy_Trips_Q3, and Divvy_Trips_Q4, have been uploaded as tables in the dataset 'Divvy_Trips'. Combining these tables resulted in a comprehensive dataset for the entire year of 2020, named "Divvy_Trips_2020_uncleaned," boasting 3,325,136 rows of data.

Next, I'll embark on the data-cleaning process with the following steps:

1. Referencing the provided schema:

![image](/images/schema.png)

2. Identifying the number of null values in each column:

![image](/images/null_value.png)

3. Determining the count of duplicates in ride_id column:

![image](/images/duplicated_row.png)

Then, 

1. Deleting rows containing null values.

2. Introducing a new column named "ride_length," calculated by subtracting the "started_at" column from the "ended_at" column, formatted as the number of minutes.

3. Deleting rows containing ride_length < 1 or ride_length >= 1440.

4. Introducing a new column named "day_of_week," indicating the day of the week each ride started, formatted with general precision (or as a number with no decimals), where 1 represents Sunday and 7 represents Saturday.

After the data cleaning process, the dataset retains 3,325,136 rows. The updated schema is as follows,

![image](/images/new_schema.png)

## Analyze and Share
Now that the data is neatly stored and ready for analysis, the next step is to consider how to organize it effectively for meaningful insights.

Key questions to address:

Is the data appropriately formatted?

What unexpected findings emerged during data exploration?

What trends or relationships are apparent in the data?

How can these insights contribute to answering crucial business questions?

To tackle these questions, I'll begin by plotting various features of the data. The initial focus will be on visualizing the total number of trips and the average duration of each trip in minutes, distinguishing between casual and member riders based on the type of bike they used.

![image](/images/Total_Trips_per_readable_type.png)

![image](/images/Average_of_ride_length_per_readable_type.png)

Analyzing the initial table and chart reveals a significant preference among both member and casual riders for docked bikes, constituting approximately 80% of their choices. A smaller percentage leans towards electric and classic bikes. It's noteworthy that there is a similarity in bike type preferences between casual and member riders.

The second plot emphasizes a key observation: casual riders tend to ride almost twice as much as members overall. Specifically, when focusing on docked bikes, casual riders clock in nearly three times more rides than members.

Our next step involves a comparative analysis of trends between casual and member riders. We'll be examining their preferences based on month, weekday, and hourly patterns, exploring the total number of trips and the average length of each trip.

![image](/images/Total_Trips_per_month.png)

![image](/images/Average_of_ride_length_per_month.png)

Examining the tables above reveals a distinct pattern in bike share usage between casual riders and members. From January to April, casual riders rarely utilize the bike share, while members ride almost ten times more frequently. Subsequently, the demand from casual riders steadily increases from May to August, reaching 270 thousand rides, mirroring a similar trend among member users. During these months, the number of trips for casual and member riders becomes nearly equal. However, starting from September to December, the demand for casual riders sharply declines, whereas for members, the decrease is gradual. 

Notably, casual riders consistently ride almost twice as much as members each month. 

![image](/images/Total_Trips_per_day_of_week.png)

![image](/images/Average_of_ride_length_per_day_of_week.png)

Clearly, casual riders are twice as likely to use the bike program on weekends compared to workdays. In contrast, members exhibit a consistent riding pattern throughout all days. Additionally, the duration of each trip for casual riders is consistently twice as long as that of members on any given day.

![image](/images/Total_Trips_per_Hour.png)

![image](/images/Average_of_ride_length_per_hour.png)

Based on the data presented in the tables, the number of trips for casual riders shows a gradual increase from 6:00 to 17:00, peaking at 125 thousand trips, followed by a gradual decrease. In contrast, for member riders, trip numbers are high in the morning, particularly from 6:00 to 8:00, experiencing a slight decline until 10:00, and then steadily increasing from 11:00 to 17:00. Additionally, casual riders tend to have longer rides per hour compared to member users.

Summing up the findings, it appears that casual riders predominantly utilize the bike share company during July, August, and September, with a preference for weekends. To delve deeper, I generated a table highlighting the most frequently used stations for casual riders, filtering by the specified months (July, August, September) and days of the week (Saturday and Sunday). The results are outlined below.

![image](/images/stations.png)

Based on the analysis of the provided table, the top 20 stations have been identified as prime locations for the bike share company's campaign to attract casual riders and convert them into members. The recommended strategy involves conducting the campaign on weekends throughout July, August, and September, specifically targeting the aforementioned high-performing stations. This approach aims to maximize the impact of the campaign and effectively encourage casual riders to join as members.

## Act

This report outlines the analysis of differences between casual and member riders and proposes targeted marketing strategies to convert casual riders into committed members. The key recommendations are as follows:

Recommendations:
##### Optimal Campaign Timing:

1. Plan the marketing campaigns strategically for the months of July, August, and September, focusing on weekends, particularly between 12:00 and 19:00 to maximize engagement.
##### Strategic Station Selection:

2. Identify and leverage the most frequented stations as primary campaign locations to enhance visibility and impact.
##### Promotional Incentives for Electric Bikes:

3. Recognize the lower appeal of electric bikes for both casual and member riders.

4. Suggest offering discounts as a persuasive incentive to increase the usage of electric bikes among both rider categories.

