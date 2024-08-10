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

### Mental Health Treatment Distribution by Gender

```python
# distribution of mental health treatment by gender
treatment_by_gender = df.groupby('Gender')['treatment'].value_counts(normalize=True).unstack()


fig, axes = plt.subplots(1, 2, figsize=(11, 7))


for i, gender in enumerate(treatment_by_gender.index):
    axes[i].pie(treatment_by_gender.loc[gender], labels=treatment_by_gender.columns, autopct='%1.1f%%', startangle=130)
    axes[i].set_title(f'{gender}')
    axes[i].axis('equal')

plt.suptitle('Mental Health Treatment Distribution by Gender', fontsize=15)
plt.show()
```
![Mental Health Treatment Distribution by Gender](images/mental_health_treatment_by_gender.png)

The plot shows the proportion of respondents who have pursued mental health treatment, categorized by gender:

Female: A larger percentage of females (69.4%) have sought mental health treatment compared to those who have not (30.6%).

Male: The data shows a more balanced distribution among males, with 46.3% having sought treatment and 53.7% not seeking treatment.
This disparity between genders suggests that females in this dataset are more likely to seek mental health treatment compared to males. Understanding these differences is crucial for addressing gender-specific barriers to mental health care.

