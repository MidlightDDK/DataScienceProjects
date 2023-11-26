# Demographic Data Analyzer
In this challenge you must analyze demographic data using Pandas. You are given a dataset of demographic data that was extracted from the 1994 Census database. Here is a sample of what the data looks like:

|    |   age | workclass        |   fnlwgt | education   |   education-num | marital-status     | occupation        | relationship   | race   | sex    |   capital-gain |   capital-loss |   hours-per-week | native-country   | salary   |
|---:|------:|:-----------------|---------:|:------------|----------------:|:-------------------|:------------------|:---------------|:-------|:-------|---------------:|---------------:|-----------------:|:-----------------|:---------|
|  0 |    39 | State-gov        |    77516 | Bachelors   |              13 | Never-married      | Adm-clerical      | Not-in-family  | White  | Male   |           2174 |              0 |               40 | United-States    | <=50K    |
|  1 |    50 | Self-emp-not-inc |    83311 | Bachelors   |              13 | Married-civ-spouse | Exec-managerial   | Husband        | White  | Male   |              0 |              0 |               13 | United-States    | <=50K    |
|  2 |    38 | Private          |   215646 | HS-grad     |               9 | Divorced           | Handlers-cleaners | Not-in-family  | White  | Male   |              0 |              0 |               40 | United-States    | <=50K    |
|  3 |    53 | Private          |   234721 | 11th        |               7 | Married-civ-spouse | Handlers-cleaners | Husband        | Black  | Male   |              0 |              0 |               40 | United-States    | <=50K    |
|  4 |    28 | Private          |   338409 | Bachelors   |              13 | Married-civ-spouse | Prof-specialty    | Wife           | Black  | Female |              0 |              0 |               40 | Cuba             | <=50K    |

You must use Pandas to answer the following questions:

-   How many people of each race are represented in this dataset? This should be a Pandas series with race names as the index labels. (`race`  column)
-   What is the average age of men?
-   What is the percentage of people who have a Bachelor's degree?
-   What percentage of people with advanced education (`Bachelors`,  `Masters`, or  `Doctorate`) make more than 50K?
-   What percentage of people without advanced education make more than 50K?
-   What is the minimum number of hours a person works per week?
-   What percentage of the people who work the minimum number of hours per week have a salary of more than 50K?
-   What country has the highest percentage of people that earn >50K and what is that percentage?
-   Identify the most popular occupation for those who earn >50K in India.

Link to the original subject: https://www.freecodecamp.org/learn/data-analysis-with-python/data-analysis-with-python-projects/demographic-data-analyzer

# My Work
In order to take care of this project, I'm going to go over each bullet point mentioned in the subject one at a time until I complete the whole work and I'll analyze the data if applicable during the process. Let's start with the first point.

## How many people of each race are represented in this dataset? This should be a Pandas series with race names as the index labels. (`race` column)
To answer this question, first, we need to import our data.


```python
import pandas as pd

df = pd.read_csv("adult.data.csv")
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>age</th>
      <th>workclass</th>
      <th>fnlwgt</th>
      <th>education</th>
      <th>education-num</th>
      <th>marital-status</th>
      <th>occupation</th>
      <th>relationship</th>
      <th>race</th>
      <th>sex</th>
      <th>capital-gain</th>
      <th>capital-loss</th>
      <th>hours-per-week</th>
      <th>native-country</th>
      <th>salary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>39</td>
      <td>State-gov</td>
      <td>77516</td>
      <td>Bachelors</td>
      <td>13</td>
      <td>Never-married</td>
      <td>Adm-clerical</td>
      <td>Not-in-family</td>
      <td>White</td>
      <td>Male</td>
      <td>2174</td>
      <td>0</td>
      <td>40</td>
      <td>United-States</td>
      <td>&lt;=50K</td>
    </tr>
    <tr>
      <th>1</th>
      <td>50</td>
      <td>Self-emp-not-inc</td>
      <td>83311</td>
      <td>Bachelors</td>
      <td>13</td>
      <td>Married-civ-spouse</td>
      <td>Exec-managerial</td>
      <td>Husband</td>
      <td>White</td>
      <td>Male</td>
      <td>0</td>
      <td>0</td>
      <td>13</td>
      <td>United-States</td>
      <td>&lt;=50K</td>
    </tr>
    <tr>
      <th>2</th>
      <td>38</td>
      <td>Private</td>
      <td>215646</td>
      <td>HS-grad</td>
      <td>9</td>
      <td>Divorced</td>
      <td>Handlers-cleaners</td>
      <td>Not-in-family</td>
      <td>White</td>
      <td>Male</td>
      <td>0</td>
      <td>0</td>
      <td>40</td>
      <td>United-States</td>
      <td>&lt;=50K</td>
    </tr>
    <tr>
      <th>3</th>
      <td>53</td>
      <td>Private</td>
      <td>234721</td>
      <td>11th</td>
      <td>7</td>
      <td>Married-civ-spouse</td>
      <td>Handlers-cleaners</td>
      <td>Husband</td>
      <td>Black</td>
      <td>Male</td>
      <td>0</td>
      <td>0</td>
      <td>40</td>
      <td>United-States</td>
      <td>&lt;=50K</td>
    </tr>
    <tr>
      <th>4</th>
      <td>28</td>
      <td>Private</td>
      <td>338409</td>
      <td>Bachelors</td>
      <td>13</td>
      <td>Married-civ-spouse</td>
      <td>Prof-specialty</td>
      <td>Wife</td>
      <td>Black</td>
      <td>Female</td>
      <td>0</td>
      <td>0</td>
      <td>40</td>
      <td>Cuba</td>
      <td>&lt;=50K</td>
    </tr>
  </tbody>
</table>
</div>



As we can see, the data was imported correctly. Now then, we can query it to get the number of people from each race.


```python
race_count = df["race"].value_counts()
race_count
```




    race
    White                 27816
    Black                  3124
    Asian-Pac-Islander     1039
    Amer-Indian-Eskimo      311
    Other                   271
    Name: count, dtype: int64



## What is the average age of men?


```python
average_age_men = round( df[ df["sex"] == "Male" ]["age"].mean(), 1)
average_age_men
```




    39.4



## What is the percentage of people who have a Bachelor's degree?


```python
percentage_bachelors = round( len( df[ df["education"] == "Bachelors" ] ) / len( df ) * 100, 1)
percentage_bachelors
```




    16.4



## What percentage of people with advanced education (Bachelors, Masters, or Doctorate) make more than 50K?

Here is the percentage of people with advanced education:


```python
higher_education = round( len( df[ ( (df["education"] == "Bachelors") | (df["education"] == "Masters") | (df["education"] == "Doctorate") ) ] ) / len(df) * 100, 1)
higher_education
```




    23.0



And between them, here is the percentage of people with a salary over 50K:


```python
higher_education_rich = round(len( df[ ( (df["education"] == "Bachelors") | (df["education"] == "Masters") | (df["education"] == "Doctorate") ) & (df["salary"] == ">50K") ] ) / len( df[ ( (df["education"] == "Bachelors") | (df["education"] == "Masters") | (df["education"] == "Doctorate") ) ] ) * 100, 1)
higher_education_rich
```




    46.5



## What percentage of people without advanced education make more than 50K?

Here is the percentage of people without advanced education:


```python
lower_education = round( len( df[ ~( (df["education"] == "Bachelors") | (df["education"] == "Masters") | (df["education"] == "Doctorate") ) ] ) / len(df) * 100, 1)
lower_education
```




    77.0



And between them, here is the percentage of people with a salary over 50K:


```python
lower_education_rich = round(len( df[ ~( (df["education"] == "Bachelors") | (df["education"] == "Masters") | (df["education"] == "Doctorate") ) & (df["salary"] == ">50K") ] ) / len( df[ ~( (df["education"] == "Bachelors") | (df["education"] == "Masters") | (df["education"] == "Doctorate") ) ] ) * 100, 1)
lower_education_rich
```




    17.4



That was to be expected but overall, people with advanced education usually earn higher salaries than people without it (46.5% > 17.4%). This can be explained by the fact that, even if the world is going towards a skill based approach towards hiring, diplomas are still a bargaining point to demand a higher pay.

## What is the minimum number of hours a person works per week?


```python
min_work_hours = df["hours-per-week"].min()
min_work_hours
```




    1



## What percentage of the people who work the minimum number of hours per week have a salary of more than 50K?


```python
num_min_workers = len(df[ ( df["hours-per-week"] == df["hours-per-week"].min()) ])
rich_percentage = round(len(df[ (df["salary"] == ">50K") & ( df["hours-per-week"] == df["hours-per-week"].min()) ]) / len(df[ ( df["hours-per-week"] == df["hours-per-week"].min()) ]) * 100, 1)
rich_percentage
```




    10.0



Knowing that in this study the minimum number of hours worked per week is 1h, I was honestly impressed to find out that there are still people able to earn a salary over 50K while working such few hours.

## What country has the highest percentage of people that earn >50K and what is that percentage?

Here is a list of all countries and the percentage of workers earning more than 50K for each one:


```python
country_percents = df[df["salary"] == ">50K"]["native-country"].value_counts() / df["native-country"].value_counts() * 100
country_percents
```




    native-country
    ?                             25.042882
    Cambodia                      36.842105
    Canada                        32.231405
    China                         26.666667
    Columbia                       3.389831
    Cuba                          26.315789
    Dominican-Republic             2.857143
    Ecuador                       14.285714
    El-Salvador                    8.490566
    England                       33.333333
    France                        41.379310
    Germany                       32.116788
    Greece                        27.586207
    Guatemala                      4.687500
    Haiti                          9.090909
    Holand-Netherlands                  NaN
    Honduras                       7.692308
    Hong                          30.000000
    Hungary                       23.076923
    India                         40.000000
    Iran                          41.860465
    Ireland                       20.833333
    Italy                         34.246575
    Jamaica                       12.345679
    Japan                         38.709677
    Laos                          11.111111
    Mexico                         5.132193
    Nicaragua                      5.882353
    Outlying-US(Guam-USVI-etc)          NaN
    Peru                           6.451613
    Philippines                   30.808081
    Poland                        20.000000
    Portugal                      10.810811
    Puerto-Rico                   10.526316
    Scotland                      25.000000
    South                         20.000000
    Taiwan                        39.215686
    Thailand                      16.666667
    Trinadad&Tobago               10.526316
    United-States                 24.583476
    Vietnam                        7.462687
    Yugoslavia                    37.500000
    Name: count, dtype: float64



Here is the highest earning country of our dataset:


```python
highest_earning_country = country_percents[ country_percents == country_percents.max() ].index[0]
highest_earning_country
```




    'Iran'



And here is the percentage of worker earning more than 50K in this country:


```python
highest_earning_country_percentage = country_percents.max()
highest_earning_country_percentage
```




    41.86046511627907



## Identify the most popular occupation for those who earn >50K in India.
Here is a sum of all people earning more than 50K in India grouped by occupations:


```python
best_occupations_india = df[ (df["native-country"] == "India") & (df["salary"] == ">50K") ]["occupation"].value_counts()
best_occupations_india
```




    occupation
    Prof-specialty      25
    Exec-managerial      8
    Other-service        2
    Tech-support         2
    Transport-moving     1
    Sales                1
    Adm-clerical         1
    Name: count, dtype: int64



And out of them, here is the occupation that has the most people over 50K:


```python
top_IN_occupation = best_occupations_india[ best_occupations_india == best_occupations_india.max() ].index[0]
top_IN_occupation
```




    'Prof-specialty'


