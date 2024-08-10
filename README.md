# Mental Health Analysis Project

## Overview
This project aims to analyze mental health trends based on a large dataset containing various factors related to mental health. The dataset includes information such as gender, country, occupation, and several indicators of mental health status. The analysis focuses on understanding patterns and correlations within the data to gain insights into mental health trends and issues.

## Dataset
The dataset used in this project is named `Mental Health Dataset.csv` and contains 292,364 entries with the following columns:

- `Timestamp`: The date and time when the data was recorded.
- `Gender`: The gender of the respondent.
- `Country`: The country of the respondent.
- `Occupation`: The occupation of the respondent.
- `self_employed`: Whether the respondent is self-employed.
- `family_history`: Whether the respondent has a family history of mental health issues.
- `treatment`: Whether the respondent has sought treatment for mental health issues.
- `Days_Indoors`: The number of days the respondent stayed indoors.
- `Growing_Stress`: Whether the respondent has experienced growing stress.
- `Changes_Habits`: Whether the respondent has noticed changes in their habits.
- `Mental_Health_History`: Whether the respondent has a history of mental health issues.
- `Mood_Swings`: Whether the respondent experiences mood swings.
- `Coping_Struggles`: Whether the respondent struggles with coping.
- `Work_Interest`: Whether the respondent has an interest in work.
- `Social_Weakness`: Whether the respondent experiences social weakness.
- `mental_health_interview`: Whether the respondent has had a mental health interview.
- `care_options`: The care options available to the respondent.

### Data Loading and Initial Exploration

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# loading the dataset
df = pd.read_csv('Mental Health Dataset.csv')

# displaying the first rows of the dataset
df.head()

# displaying information about the dataset
df.info()

# checking for missing values
df.isnull().sum()

# filling missing values in 'self_employed' with 'Unknown'
df['self_employed'].fillna('Unknown', inplace=True)
```

## Exploratory Data Analysis
### Gender Distribution
The first step in the exploratory data analysis was to understand the distribution of genders within the dataset. A bar plot was generated to visualize this distribution, as shown below:

```python
# creating a plot of gender distribution
plt.figure(figsize=(10, 6))
sns.countplot(data=df, x='Gender')
plt.title('Distribution of Gender')
plt.xlabel('Gender')
plt.ylabel('Count')
plt.show()
```

![Gender Distribution](images/gender_distribution.png)

The plot shows that there is a significant gender imbalance in the dataset, with the majority of respondents identifying as male. This disparity is important to note as it may influence the outcomes of further analysis, particularly when looking into gender-specific trends or mental health issues.