# Student-Data-Analysis

This project examines the financial circumstances facing students whose data was included in the data. The data should provide an idea of the direction of students' cash flow, through the use of matplotlib and seaborn line and bar plots.

## Downloading the Dataset

!pip install jovian opendatasets --upgrade --quiet

dataset_url = 'https://www.kaggle.com/datasets/sumanthnimmagadda/student-spending-dataset'

import opendatasets as od
od.download(dataset_url)

"""The dataset has been downloaded and extracted."""

data_dir = './student-spending-dataset'

import os
os.listdir(data_dir)

project_name = "student-spending-data-analysis" 

!pip install jovian --upgrade -q

import jovian

jovian.commit(project=project_name)

import pandas as pd

## Cleaning the dataset

student_df = pd.read_csv(data_dir + "/student_spending (1).csv")

student_df.info

student_df.describe()

student_df

with open('./student-spending-dataset/student_spending (1).csv') as file:
  file_contents = file.readlines()
  print(file_contents)

def parse_headers(header_line):
  return header_line.strip().split(',')

file_contents[0]

headers = parse_headers(file_contents[0])
headers

student_df.drop_duplicates()

student_df.dropna()

import jovian

jovian.commit()

"""importing`matplotlib.pyplot` and `seaborn`."""

student_df

import seaborn as sns
import matplotlib
import matplotlib.pyplot as plt
%matplotlib inline

sns.set_style('whitegrid')
matplotlib.rcParams['font.size'] = 14
matplotlib.rcParams['figure.figsize'] = (6,3)
matplotlib.rcParams['figure.facecolor'] = '#00000000'

## Data Exploration/Analysis

student_df.major.unique()

sns.lineplot(x='year_in_school', y='housing', marker='o', ls='-', color='Red', ms=4, linewidth=1, ci=None, errorbar=None, data=student_df)
plt.title("Average Monthly Housing Cost by Academic Year")
plt.xlabel("Academic Year", fontsize=8.5)
plt.ylabel("Average Monthly Housing Cost (in USD)", fontsize=8.5)
plt.yticks(fontsize=10)
plt.xticks(fontsize=10)
sns.set_theme(font_scale=1)
sns.set_style("white")
plt.figure(figsize=(10,7))
plt.show();

sns.lineplot(x='major', y='tuition', data=student_df, marker='o',ms=4, ls='-', dashes=True, ci=None)
plt.title("Average Tuition Cost by Major")
plt.xlabel("Major", fontsize=8.5)
plt.ylabel("Average Tuition Cost (in USD)", fontsize=8.5)
plt.yticks(fontsize=10)
plt.xticks(fontsize=10)
sns.set_theme(font_scale=1)
sns.set_style("white")
plt.figure(figsize=(10,7))
plt.show();

import numpy as np
student_df.to_numpy()
year_in_school=student_df['year_in_school']
avg_monthly_income =student_df.groupby('year_in_school').mean()

sns.lineplot(x='year_in_school', y='monthly_income', color='r', marker=None,ms=5, ls='-', linewidth=3, data=student_df, ci=None, errorbar=None)
plt.title("Average Monthly Income by Academic Year")
plt.xlabel("Academic Year", fontsize=8.5)
plt.ylabel(" Average Monthly Income (in USD)", fontsize=8.5)
plt.yticks(fontsize=10)
plt.xticks(fontsize=10)
sns.set_theme(font_scale=1)
sns.set_style("white")
plt.figure(figsize=(5,5))
plt.show()

sns.barplot(x='tuition', y='major', data=student_df, hue='major');
plt.xlabel("Average Cost of Tuition", fontsize=8.5)
plt.ylabel("Major", fontsize=8.5)
plt.xticks(fontsize=10)
plt.yticks(fontsize=10)
plt.title("Average Cost of Tuition by Major")
plt.figure(figsize=(10,7))
plt.show();

plt.hist(student_df.major, bins=5, color='pink', ec='green', lw=3)
plt.title("Distribution of Students by Major")
plt.xlabel('Major')
plt.ylabel('Number of Students')
plt.rc('axes', labelsize=8)    # fontsize of the x and y labels
plt.rc('xtick', labelsize=9)    # fontsize of the tick labels
plt.rc('ytick', labelsize=9)    # fontsize of the tick labels
plt.figure(figsize=(10,7))
plt.show();

import jovian

jovian.commit()

# Which major has the highest number of matriculated students?
# Biology

plt.hist(student_df.major, bins=5, color='pink', ec='green', lw=3)
plt.title("Distribution of Students by Major")
plt.xlabel('Major')
plt.ylabel('Number of Students')
plt.rc('axes', labelsize=8)    # fontsize of the x and y labels
plt.rc('xtick', labelsize=9)    # fontsize of the tick labels
plt.rc('ytick', labelsize=9)    # fontsize of the tick labels
plt.figure(figsize=(10,7))
plt.show();

# Which major costs the most in tuition? Psychology
sns.barplot(x='tuition', y='major', data=student_df, hue='major');
plt.xlabel("Average Cost of Tuition", fontsize=8.5)
plt.ylabel("Major", fontsize=8.5)
plt.xticks(fontsize=10)
plt.yticks(fontsize=10)
plt.title("Average Cost of Tuition by Major")
plt.figure(figsize=(10,7))
plt.show();

# During academic year do students gain the highest income? Freshman
sns.lineplot(x='year_in_school', y='monthly_income', color='r', marker=None,ms=5, ls='-', linewidth=3, data=student_df, ci=None, errorbar=None)
plt.title("Average Monthly Income by Academic Year")
plt.xlabel("Academic Year", fontsize=8.5)
plt.ylabel(" Average Monthly Income (in USD)", fontsize=8.5)
plt.yticks(fontsize=10)
plt.xticks(fontsize=10)
sns.set_theme(font_scale=1)
sns.set_style("white")
plt.figure(figsize=(5,5))
plt.show()

# During which year do students pay the least for housing? Sophomore
sns.lineplot(x='year_in_school', y='housing', marker='o', ls='-', color='Red', ms=4, linewidth=1, ci=None, errorbar=None, data=student_df)
plt.title("Average Monthly Housing Cost by Academic Year")
plt.xlabel("Academic Year", fontsize=8.5)
plt.ylabel("Average Monthly Housing Cost (in USD)", fontsize=8.5)
plt.yticks(fontsize=10)
plt.xticks(fontsize=10)
sns.set_theme(font_scale=1)
sns.set_style("white")
plt.figure(figsize=(10,7))
plt.show();

import jovian

jovian.commit()

# Conclusion**


It appeared that even though biology students make up most of the student body, they pay the least in tuition.
However, although psychology students make up the smallest portion of the student body, they pay the highest in tuition costs on average.
Surprisingly, the underclassman years are the most affordable years, as shown by students having the highest average income during freshman year and paying the lowest housing costs on average during their sophomore year.
In addition, the school needs to increase aid offered to students, as there is a significant discrepancy between average tuition costs and average financial aid students receive. This is shown by the lack of intersection between the two axes.
"""

import jovian

jovian.commit()


