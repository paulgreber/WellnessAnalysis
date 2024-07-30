# Bellabeat Wellness Tracker Analysis

This project is being done as part of the Google Data Analytics capstone project. It serves as an example of the skills that have been learned during the entire course.

During this project data will be collected, prepared, processed and analyzed. Visualizations will be created, conclusions from the data will be determined and insights will be presented to potential stakeholders.

## Background

Bellabeat is a high-tech manufacturer of health-focused products for women. Bellabeat's fitness trackers collect a large amount of data from their customers. It is believed that this data can provide insights into how consumers use Bellabeat products and guide the marketing strategy for the company.

## Objective

Analyze the data from Bellabeat fitness trackers and identify any trends that occur. In particular, we will be looking at trends which differentiate those with a normal BMI to those with an overweight BMI.

## Preparation

### Data Sources

The data for this exercise come from [FitBit Fitness Tracker Data](https://www.kaggle.com/datasets/arashnic/fitbit), a dataset available on Kaggle which contains data from 30 Fitbit users.

The documentation for what exactly each column in the dataset means can be found [here](https://www.fitabase.com/media/1930/fitabasedatadictionary102320.pdf)

The data for this dataset was obtained by consenting users and is available freely under the public domain.

This data is believed to be credible and contain no bias.

The data sources that we will be looking at will be:

* **minuteStepsNarrow_merged.csv**: The number of steps moved on a minute by minute basis.

* **minuteIntensitiesNarrow_merged.csv**: The intensity level on a minute by minute basis.

* **minuteSleep_merged.csv**: The sleep state of a person on a minute by minute basis.

* **weightLogInfo_merged.csv**: The weight of a person on a given day.

### Privacy Issue

There should be no privacy issues in this data as no names, credit card numbers or email addresses are present. The data does contain a user `Id` which allows us to cross reference individuals, however this is a ten digit number and provides no mechanism to determine who that number might represent.

## Data Processing

### Tools Used

For this exercise, Python will be used to process the data. It has a wide range of tools for working with and validating datasets (`Pandas`) and creating visualizations (`Seaborn`).

### Data Integrity

Each of the datasets are examined for the following conditions:

* The presence of any NULL values in any columns
* Checking that the date and time values are reasonable and coincide with the other datasets.
* Checking that minimum and maximum values are reasonable, that values that shouldn't be negative (steps walked) aren't.

During this check the following anomalies were detected:

* In the body weight dataset, most entries contained a NULL value in the `Fat` column. As a result, the entire `Fat` column was dropped from the dataset.

## Data Transformations and Explanation

### Day of Week & Time of Day

Each entry in these datasets contain a timestamp which identifies when a record was made. From this timestamp we will extract the day of the week (Monday, Tuesday, etc) and the time of day (Morning, Afternoon, Evening, Night) and use that in our analysis.

### BMI

A large portion of our analysis will be done comparing two groups of users, those with normal BMIs and those with overweight BMIs. In the case of this analysis, we classify a normal BMI as being between 18.5 and 25 and an overweight BMI as being between 25 and 30.

The rationale for this grouping comes from [this source](https://www.builtlean.com/bmi-chart/)

### Intensity Levels

From the [documentation](https://www.fitabase.com/media/1930/fitabasedatadictionary102320.pdf) which describes that dataset, `Intensity` data is categorical with values of 0 to 3 representing different activity levels:

0. Sedentary
1. Light
2. Moderate
3. Very Active

## Analysis

### BMI as a Health Metric

Our analysis will focus on examining how the wellness habits of users differ, based on their BMI grouping. The theory being that users with a normal BMI have better habits than those who are overweight. We will start by looking at the number of users in each BMI group to verify that we can do a fair analysis.

![Count of Users by BMI Group](/analysis/bmi_user_count.png)

Seeing that there are so few users in the `extremely_obese` group, we will be continuing the rest of our analysis using the `normal` and `overweight` groups only.

### Daily Steps

The following graphs will show how many steps a day were taken and when those steps were taken.

![Daily Steps](/analysis/steps_daily.png)

![Daily Steps - Time of Day](/analysis/steps_time_of_day.png)

![Daily STeps - Day of Week](/analysis/steps_day_of_week.png)

Both groups of users take comparable number of steps in a day, however the main difference is that those in the normal BMI group were often more consistent with how many steps they took, while those in the overweight BMI group tended to fluctuate more.

### Intensity

We will be excluding Sedentary activity from our analysis because Sedentary activity is by definition, not being active. One could also infer that any time not being active is spent being sedentary.

The graphs below show how many hours of intensive activity users engaged in, what the level of the activity was and when they were most active.

![Intensity Daily](/analysis/intensity_daily.png)

![Intensity Time of Day Normal](/analysis/intensity_time_of_day_normal.png)

![Intensity Time of Day Overweight](/analysis/intensity_time_of_day_overweight.png)

![Intensity Day of Week Normal](/analysis/intensity_day_of_week_normal.png)

![Intensity Day of Week Overweight](/analysis/intensity_day_of_week_overweight.png)

We can make the following observations from this analysis:

1. Users with normal BMIs obtain more hours and are more consistent with the number of light intensity hours than users in the overweight group.

2. Users in the overweight group obtain more hours of very activity intensity than those in the normal BMI group.

This could indicate that overweight users are opting to perform higher intensity workouts in a brief period of time, while users with a normal BMI opt instead to do more light intensity activities.

### Sleep

The following graphs will show how many hours of sleep users of different BMIs get and when they get those hours of sleep.

![Sleep Daily](/analysis/sleep_daily.png)

![Sleep Time of Day Normal](/analysis/sleep_time_of_day_normal.png)

![Sleep Time of Day Overweight](/analysis/sleep_time_of_day_overweight.png)

![Sleep Day of Week Normal](/analysis/sleep_day_of_week_normal.png)

![Sleep Day of Week Overweight](/analysis/sleep_day_of_week_overweight.png)

Users in the normal BMI group get more sleep and are more consistent with their sleep than users in the overweight group.

## Summary

Users in the normal BMI group could be categorized as:

* More consistent with the number of steps walked in a day than other groups.
* Performed more light intensity activities than other groups.
* Got more sleep more often than other groups.

Users in the overweight BMI group could be categorized as:

* Less consistent with the number of steps walked in a day compared to other groups.
* Performed more high intensity activities than other groups.
* Got less sleep and were less consistent with the amount of sleep they received than other groups.

## Conclusion

From our analysis, we can see that users with normal BMIs are consistent in making small positive health choices.

* They are opting to do more light intensity activities than high intensity ones.
* They are regularly getting their steps in.
* They are consistently getting a good nights sleep.

Therefore, if someone wanted to be healthier they should be looking to make small but consistent changes to their lifestyle.

## Action to Take

The recommendation to the marketing department would be to promote Bellabeat products as a tool to help maintain small but impactful lifestyle habits.

## Future Analysis

The number of users we were able to analyze was small and only contained two BMI groups, having more data from a wider range of individuals may help us reach better conclusions.

Also, fitness and health is a complicated subject with a lot of different factors at play. The fitness trackers can only measure how much energy they are excreting, but not how much they are consuming. Having more nutritional information could help in identifying better trends.

And finally, our analysis was based on the assumption that people with normal BMIs are healthier than those with an overweight BMI. But BMI isn't always the best indicator of how healthy a person is. Having some other metric to use for health or to differentiate between users could result in a more accurate analysis.
