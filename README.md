# Bellabeat Data Analysis Portfolio
## Part 1: Background & Overview
Established in 2014, Bellabeat has now become a leading, women-focused health & wellness smart device manufacturer. The company boasts an expansive product line and is primarily known for its Leaf smart jewelry wearables, the Time watch, and the Spring hydration bottle. Through these products, Bellabeat aims to use technology to enchance the lives of women globally. 

As a junior data analyst on Bellabeat’s marketing team, I was tasked with analyzing smart device usage data to uncover insights into user behavior. Based on these findings, I developed data-driven recommendations to inform and enhance Bellabeat’s overall marketing strategy, which were later presented to the executive team.

The insights and recommendations were based on three key areas/demographics:
- **User Sleep & Weight Patterns:** A time series analysis of users sleep and weight changes over 30 days.
- **User Physical Level/Activity Assessment:** An assessment of a user's overall physical activity taking into account their Daily Steps and Metabolic Equivalent of Tasks (METs).
- **Smart Device Feature Usage:** An evaluation of what proportion of total users used certain features such as sleep and/or weight tracking. 

## Part 2: Original Data Structure
The Bellabeat dataset is composed of smart device data tracking users through their activity, caloric intake, sleep behaviours, and weight logging. The data was tracked over 30 days, starting from 04/12/2016 and ending on 05/12/2016.

The orginal smart device data is composed as shown below:

<table>
<tr>
<td valign="top" width="50%">

### weightLogInfo_merged

| Column Name      | Data Type |
|------------------|-----------|
| Id               | int64     |
| Date             | datetime  |
| WeightKg         | float64   |
| WeightPounds     | float64   |
| Fat              | float64   |
| BMI              | float64   |
| IsManualReport   | bool      |
| LogId            | int64     |

</td>
<td valign="top" width="50%">

### sleepDay_merged

| Column Name         | Data Type |
|---------------------|-----------|
| Id                  | int64     |
| SleepDay            | datetime  |
| TotalSleepRecords   | int64     |
| TotalMinutesAsleep  | int64     |
| TotalTimeInBed      | int64     |

</td>
</tr>

<tr>
<td valign="top">

### dailyActivity_merged

| Column Name               | Data Type |
|---------------------------|-----------|
| Id                        | int64     |
| ActivityDate              | date      |
| TotalSteps                | int64     |
| TotalDistance             | float64   |
| TrackerDistance           | float64   |
| LoggedActivitiesDistance  | float64   |
| VeryActiveDistance        | float64   |
| ModeratelyActiveDistance  | float64   |
| LightActiveDistance       | float64   |
| SedentaryActiveDistance   | float64   |
| VeryActiveMinutes         | int64     |
| FairlyActiveMinutes       | int64     |
| LightlyActiveMinutes      | int64     |
| SedentaryMinutes          | int64     |
| Calories                  | int64     |

</td>
<td valign="top">

### dailySteps_merged

| Column Name     | Data Type |
|-----------------|-----------|
| Id              | int64     |
| ActivityDay     | date      |
| StepTotal       | int64     |

<br/>

### minuteMETsNarrow_merged

| Column Name        | Data Type |
|--------------------|-----------|
| id                 | int64     |
| ActivityMinute     | datetime  |
| METs               | int64     |

</td>
</tr>
</table>

*Note: minuteMETsNarrow_merged was not uploaded due to file size. However, it was cleaned using Python. 

## Part 3: Cleaning & Preprocessing

During the initial exploratory data analysis, I did not find any major data quality issues such as missing values or duplicated rows. However, I still implemented a small Python cleaning script using Pandas to automatically handle any potential inconsistencies that may not have been immediately visible during manual inspection.

To streamline the analysis across key areas (sleep/weight patterns, fitness activity, and feature usage), I applied several data transformations. I removed rows that were irrelevant to the project and converted datetime columns to date-only formats. This not only simplified time-based analysis but also prevented formatting inconsistencies when importing the data into Power BI and working with it in Power Query.

Using SQL, I also joined multiple tables to create new, analysis-ready datasets that highlighted specific insights and relationships. In particular, I generated a weight_log_usage table and a sleep_log_usage table to more effectively examine usage patterns and behavioral trends.

## Part 4: Cleaned Data Structure

After transforming and cleaning the data, the final structure of the tables used for analysis looked as shown below:

<table>
<tr>
<td valign="top" width="50%">

### weight_over_time

| Column Name      | Data Type |
|------------------|-----------|
| id               | int64     |
| logdate          | date      |
| weightpounds     | float64   |
| bmi              | float64   |

</td>
<td valign="top" width="50%">

### sleep_over_time

| Column Name         | Data Type |
|---------------------|-----------|
| id                  | int64     |
| sleepday            | date      |
| totalhoursasleep    | float64   |
| totalhoursinbed     | float64   |

</td>
</tr>

<tr>
<td valign="top">

### categorized_user_activity

| Column Name               | Data Type |
|---------------------------|-----------|
| acitivty_type             | varchar   |
| total                     | int64     |
| user_percentage           | float64   |

</td>
<td valign="top">

### dailySteps

| Column Name     | Data Type |
|-----------------|-----------|
| Id              | int64     |
| StepTotal       | float64   |

</td>
</tr>

<tr>
<td valign="top">

### sleep_log_usage

| Column Name         | Data Type |
|---------------------|-----------|
| usage_level         | varchar   |
| user_count          | int64     |
| user_percentage     | float64   |
| total_user_percent..| float64   |

</td>
<td valign="top">

### weight_log_usage

| Column Name         | Data Type |
|---------------------|-----------|
| usage_level         | varchar   |
| user_count          | int64     |
| user_percentage     | float64   |
| total_user_percent..| float64   |

</td>
</tr>

<tr>
<td valign="top">

### METS_3

| Column Name         | Data Type |
|---------------------|-----------|
| Id                  | int64     |
| Date                | date      |
| Day                 | varchar   |
| Hour                | int64     |
| METs                | int64     |

</td>
<td valign="top">

### METs_avg

| Column Name         | Data Type |
|---------------------|-----------|
| ActivityMinute      | time      |
| METs                | float64   |

<br/>

### avg_sleep_per_id

| Column Name         | Data Type |
|---------------------|-----------|
| Id                  | int64     |
| avg_sleep           | float64   |

</td>
</tr>
</table>

*Note: METS_3 was not uploaded due to file size. However, it was cleaned using Python and uploaded to Power BI.  

## Part 5: Executive Summary (Overview)

An overview summary shows that Bellabeat users are more active than the average, showcasing a customer importance on health and fitness. However, engagement with sleep and weight features remains relatively low. This gap could highlight an opportunity to increase app usage and retention. Using user behaviour patterns, such as peak METs, to allign Bellabeat's product features and marketing focus, would translate into long-term user value and stronger habit formation. 

Some quick insights:
- Roughly 70% of users partake in at least some form of light activity.
- Many users demonstrate poor sleep quality, getting <7 hours and spend 1–2 hours awake in bed.
- Out of the 33 total participants, only 8 had substantial usage of weight logging.
- Average METs generally peaked around 5-7 PM during the week. 

The full interactive Power BI dashboard can be downloaded [https://github.com/shauqt/Bellabeat-Case-Study-Data-Analysis/blob/main/Bellabeat.pbix](url)

## Part 6: Deeper Analysis 

## Part 7: Shareholder Recommendations

