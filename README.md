# Bellabeat Data Analysis Portfolio
## Part 1: Background & Overview
Established in 2014, Bellabeat has now become a leading, women-focused health & wellness smart device manufacturer. The company boasts an expansive product line and is primarily known for its Leaf smart jewelry wearables, the Time watch, and the Spring hydration bottle. Through these products, Bellabeat aims to use technology to enchance the lives of women globally. 

As a junior data analyst on Bellabeat’s marketing team, I was tasked with analyzing smart device usage data to uncover insights into user behavior. Based on these findings, I developed data-driven recommendations to inform and enhance Bellabeat’s overall marketing strategy, which were later presented to the executive team.

The insights and recommendations were based on three key areas/demographics:
- **User Sleep & Weight Patterns:** A time series analysis of users sleep and weight changes over 30 days.
- **User Physical Level/Activity Assessment:** An assessment of a user's overall physical activity taking into account their Daily Steps and Metabolic Equivalent of Tasks (METs).
- **Smart Device Feature Usage:** An evaluation of what proportion of total users used certain features such as sleep and/or weight tracking. 

## Part 2: Original Data Structure
The Bellabeat dataset is composed of smart device data tracking users through their activity, caloric intake, sleep behaviours, and weight logging. 

The orginal smart device data is composed as shown below:

 <table>
<tr>
<td valign="top" width="50%">

### weightLogInfo_merged

| Column Name      | Data Type |
|------------------|-----------|
| Id               | int64     |
| Date             | date      |
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
| SleepDay            | date      |
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

### weight_over_time

| Column Name     | Data Type |
|-----------------|-----------|
| Id              | int64     |
| logdate         | date      |
| weightpounds    | float64   |
| bmi             | float64   |

<br/>

### sleep_over_time

| Column Name        | Data Type |
|--------------------|-----------|
| id                 | int64     |
| sleepday           | date      |
| totalhoursasleep   | float64   |
| totalhoursinbed    | float64   |

</td>
</tr>

<tr>
<td valign="top">

### kpi_2_avg_sleep_per_Id

| Column Name | Data Type |
|-------------|-----------|
| Id          | int64     |
| avg_sleep   | float64   |

</td>
<td valign="top">

### categorized_user_activity

| Column Name     | Data Type |
|-----------------|-----------|
| activity_type   | string    |
| total           | int64     |
| user_percentage | float64   |

</td>
</tr>
</table>


## Part 3: Cleaning & Preprocessing

## Part 4: Cleaned Data Structure

## Part 5: Executive Summary (Overview)

## Part 6: Deeper Analysis + Visuals

## Part 7: Shareholder Recommendations

