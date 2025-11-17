# Bellabeat Data Analysis Portfolio
## Part 1: Background & Overview
Established in 2014, Bellabeat has now become a leading, women-focused health & wellness smart device manufacturer. The company boasts an expansive product line and is primarily known for its Leaf smart jewelry wearables, the Time watch, and the Spring hydration bottle. Through these products, Bellabeat aims to use technology to enchance the lives of women globally. 

As a junior data analyst on Bellabeat’s marketing team, I was tasked with analyzing smart device usage data to uncover insights into user behavior. Based on these findings, I developed data-driven recommendations to inform and enhance Bellabeat’s overall marketing strategy, which were later presented to the executive team.

The insights and recommendations were based on three key areas/demographics:
- **User Sleep & Weight Patterns:** A time series analysis of users sleep and weight changes over 30 days.
- **User Physical Level/Activity Assessment:** An assessment of a user's overall physical activity taking into account their Daily Steps and Metabolic Equivalent of Tasks (METs).
- **Smart Device Feature Usage:** An evaluation of what proportion of total users used certain features such as sleep and/or weight tracking. 

---

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

---

## Part 3: Cleaning & Preprocessing

During the initial exploratory data analysis, I did not find any major data quality issues such as missing values or duplicated rows. However, I still implemented a small Python cleaning script using Pandas to automatically handle any potential inconsistencies that may not have been immediately visible during manual inspection.

To streamline the analysis across key areas (sleep/weight patterns, fitness activity, and feature usage), I applied several data transformations. I removed rows that were irrelevant to the project and converted datetime columns to date-only formats. This not only simplified time-based analysis but also prevented formatting inconsistencies when importing the data into Power BI and working with it in Power Query.

Using SQL, I also joined multiple tables to create new, analysis-ready datasets that highlighted specific insights and relationships. In particular, I generated a weight_log_usage table and a sleep_log_usage table to more effectively examine usage patterns and behavioral trends.

The Python file can be downloaded [here](https://github.com/shauqt/Bellabeat-Case-Study-Data-Analysis/blob/main/bellabeat.ipynb).

The SQL queries can be accessed in this [folder](https://github.com/shauqt/Bellabeat-Case-Study-Data-Analysis/tree/main/SQL%20queries).

---

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

---

## Part 5: Executive Summary (Overview)

An overview summary shows that Bellabeat users are more active than the average, showcasing a customer importance on health and fitness. However, engagement with sleep and weight features remains relatively low. This gap could highlight an opportunity to increase app usage and retention. Using user behaviour patterns, such as peak METs, to allign Bellabeat's product features and marketing focus, would translate into long-term user value and stronger habit formation. 

Here is the Power BI dashboard:

<img width="1412" height="794" alt="dashboard_overview" src="https://github.com/user-attachments/assets/d04335b3-4f0f-4932-8192-6e036f2580be" />

Some quick insights:
- Roughly 70% of users partake in at least some form of light activity, with the average number of daily steps taken by users being 7520.
- Many users demonstrate poor sleep quality, getting <7 hours and spend 1–2 hours awake in bed.
- Out of the 33 total participants, 24 utilized sleep logging features whereas only 8 had substantial usage of weight logging.
- Average METs generally peaked around 5-7 PM during the week.

The full interactive Power BI dashboard can be downloaded [here](https://github.com/shauqt/Bellabeat-Case-Study-Data-Analysis/blob/main/Bellabeat.pbix).

## Part 6: Deeper Analysis 

### Sleep Patterns

Averaging the total sleep duration of users shows that on average, users got about **6.29 hours of sleep** per night. In addition, when comparing the amount of time spent in bed versus the amount of time asleep in, users are seen often spending an **additional 1-2 hours awake while in bed**. This pattern continued throughout the 30 days of the experiment as seen in _Figure 1_. These two insights indicate that the users have **low sleep efficieny**, potentially derviving from stress, poor bedtime routines, and lengthly late-night screen exposure.

<img width="605" height="579" alt="image" src="https://github.com/user-attachments/assets/9a2caae3-be0e-4c2d-808c-f5ec575cf1fb" />

_Figure 1: Average Hours Asleep Versus Hours in Bed Over 30 Days_

**Key Takeaways:**
- Average **time spent in bed is consistently 2 hours greater than asleep**.
- Extended poor sleep behaviours can lead to negative health consequences.
- **Recommendation:** Introduce and promote healthy night-time, wind-down routines and methods to reduce screen time.

---

### Weight Tracking

As noted in the overview, **only 8 of the 33 participants** (approximately **24%**) made use of the weight-tracking feature. Although usage is low, two participants logged enough entries to support a 30-day time-series analysis. Their data indicates an overall downward trend in weight, highlighting a small but meaningful segment of engaged users. This presents an opportunity for Bellabeat to better support and potentially expand this motivated user group.

<img width="629" height="533" alt="weight_over_time_a" src="https://github.com/user-attachments/assets/c105011e-4950-4094-8a69-2a92084dc500" />

_Figure 2a: User A Weight Over 30 Days_

<img width="612" height="481" alt="weight_over_time_b" src="https://github.com/user-attachments/assets/aca092dd-e14d-4b77-8731-7b4c5f5164de" />

_Figure 2b: User B Weight Over 30 Days_

**Key Takeaways:**
- Minimal adoption of the weight-tracking feature suggests that users may not perceive it as essential or may find it unintuitive.
- Yet, those who consistently used it demonstrated meaningful health improvements, including steady weight reduction.
- **Recommendation:** Bellabeat should enhance and promote the feature by offering clearer value messaging, easier data entry, and personalized progress feedback to encourage more users to engage with weight management tools.

---

### Activity Levels

Approximately **70% of users log daily physical activity**, while only 20% have been categorized as "Active" or "Very Active". The various categories were created based on the daily steps users took, with Active being defined as greater than 10,000 daily steps and Very Active being defined as greater than 12,500. While not a perfect metric to assess activity levels, given the data, it was the most effective method to categorize users into different demographics.

Overall, many smart device users demonstrate a high baseline engagement with fitness, making them an ideal market for Bellabeat to continue supporting and providing new incentives/features.

<img width="601" height="430" alt="activity_level" src="https://github.com/user-attachments/assets/f134f650-f677-4da8-b2df-4c9246cbe3ca" />

_Figure 3: Percentage of Users By Activity Level_

**Key Takeaways:**
- Users are generally active on a consistant basis, but not many are considered "Active". This suggests many users track their activity, but are not reaching the recommended daily movement levels.
- Opportunity exists to expand in this market and create a loyal customer base that chooses Bellabeat for their fitness needs.
- **Recommendation:** Implement features like activity reminders, milestone badges, coaching tips, and motivational nudges/challenges to help users reach their health goals, develop a more personalized experience, and increase engagement from users.

---

### METs Analysis

Delving deeper into activity and fitness, is the Metabolic Equivalent of Tasks (METs) metric. METs is a standardized way to measure how much energy the body uses during physical activity. For reference, 1 MET is the body at rest. Therefore, the higher the METs value, the greater the physical activity.

Analyzing users' average METs revealed that user peak activity levels occured between 5 PM and 7 PM. This suggests that many of the participants are either students or working professionals and typically excerised after work/school.

<img width="626" height="644" alt="mets_by_time_of_day" src="https://github.com/user-attachments/assets/d5699630-382c-46ca-9435-af0c71fe13d9" />

_Figure 4a: Average METs by Time of Day_

Looking at the data on a weekly basis, the pattern of METs peaking after work hours remained consistent throughout the weekdays. However, on weekends this pattern shifts, with peak MET levels occurring in the early afternoon (around 1 PM). This suggests that most users likely work standard daytime schedules and prefer to exercise earlier in the day during their time off.

<img width="841" height="714" alt="mets_weekly_heatmap" src="https://github.com/user-attachments/assets/5e3f4259-976b-49a8-a436-d747eeaf61cb" />

_Figure 4b: Weekly METs Heatmap_

**Key Takeaways:**
- Average METs peaks roughly between 5-7 PM during the weekdays. On weekends, METs peak ealier around 1 PM.
- Indicates a majority of users work standard schedules and exercise after work/school.
- **Recommendations:** Develop personalized coaching features that help users balance work and fitness. Examples include after-work activity guidance, healthy routine-building prompts, and weekend workout suggestions based on user behavior patterns.

--- 

## Part 7: Shareholder Recommendations

Based on user demographics, behaviours, and engagement, it is recommended that Bellabeat should shift and market itself as a **companion that aims to empower and improve the daily lives of users**. The company can accomplish this by making the following changes:
- **Enhance sleep support through structured habit-building tools.** Given that users average 6.29 hours of sleep and spend 1–2 hours awake in bed, Bellabeat can introduce features such as wind-down routines, screen-time reduction challenges, and guided breathing exercises. Helping users form healthier evening habits could meaningfully improve sleep quality and overall engagement.

- **Increase weight-tracking adoption through positive, low-pressure gamification.** Only 24% of users log their weight, suggesting low engagement with this feature. Reframing weight logging as a consistency-based habit—supported by streaks, badges, and trend visualization—can make the feature more approachable and reduce performance-related anxiety, leading to more consistent usage.

- **Offer adaptive fitness programs aligned with user behavior patterns.** With 70% of users logging activity and peak MET levels occurring between 5–7 PM, Bellabeat can deliver timely nudges such as post-work challenges, hydration reminders, or reflective journal prompts. These adaptive programs would help users build sustainable routines that fit naturally into their daily schedules.

- **Optimize behavior-driving notifications using A/B-tested timing.** Bellabeat can test different reminder delivery windows—such as morning hydration prompts or evening mindfulness messages—to identify the most effective times for influencing user behavior and maximizing engagement.

- **Expand lifestyle support through healthy content and device integrations.** Introducing curated “Bellabeat Recipes” or partnering with smart scales and complementary wearables can deepen the Bellabeat ecosystem and help users form healthier routines beyond physical activity tracking alone.

- **Enable more targeted product development through enhanced segmentation.** Collecting demographic variables in future datasets would allow Bellabeat to segment users (e.g., early-career professionals, parents, midlife wellness users) and tailor features, content, and marketing strategies to specific groups more effectively.

---

## Part 8: Future Steps & Improvements



