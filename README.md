
# DO REVIEWS AFFECT BOX OFFICE PERFORMANCE?

---

This is the project I worked on for my Master's Thesis. 

The central research question was "TO WHAT EXTENT DO REVIEWS INFLUENCE THE 
BOX OFFICE LEGS OF THEATRICAL MOVIE RELEASES, AND HOW DOES BUZZ INFLUENCE 
THIS RELATIONSHIP?".

And the goal was to expand on the research into the long-term performance of 
movies in the box office. It has been a widely debated topic due to the rise
of streaming services. Which has caused less traffic towards the cinemas.
Therefore, it brings up the question of what can actually improve long-term
box office performance. 

To narrow down the scope I wanted to focus on the consumer. What factors by the
consumer can affect a movie's performance. Since at the end of the day that is
the target group. In this case I wanted to focus on the abundance and the 
sentiment. Abundance as in volume of consumer engagement in the form of a
review. And sentiment as in the emotion of consumer engagement. As well as the
overall buzz around a movie which signifies the overall engagement. 

---

## Preliminary Information

The data cleaning, wrangling, and analysis was mostly performed in Excel and R.
To replicate my findings I would suggest using R since all my code is located 
in R notebooks. 

Below I will describe each file to provide context for the purpose of 
replicating the same findings I got during my research. 

Cleaning_Filtered.Rmd: This is the more limited data cleaning file. By limited
I mean that it does not include all of the data cleaning I performed. This is 
due to the large CSV files that required importing and cleaning which cannot be
pushed to Github. For that reason I created this file so that you can still 
import the final analysis datasets but excluding the cleaning process which
involved importing massive CSV files. 

Cleaning.Rmd: This is the original cleaning file that I used for my research. 
It contains all the steps I took to clean my datasets.

Analysis.Rmd: This is a notebook with all the analysis I performed on the data.
From descriptive analysis to more complex regressions. It also contains the
assumption tests I conducted.

Buzz/: This folder contains Google Trends data for all the movies within my 
sample. 335 movies to be specific. 

movies.csv: Contains various convenient movie indicators ranging that were used
for cleaning and merging. Such as movieId, movieYear and movieTitle. As well as
the variable release_date_theaters that was used to calculate box office legs. 

revenues_clean.csv: Contains financial information which was used as a indicator
for performance. As well as control variables such as Genre and Season. 

critic_analysis_data.csv: The final critic review analysis dataset. This is the
dataset after all the cleaning. The original dataset is too large in file size 
to be able to be pushed to Github. 

user_analysis_data.csv: The final user review analysis dataset. This is the
dataset after all the cleaning. The original dataset is too large in file size 
to be able to be pushed to Github. 

## How to Replicate Findings?




# DO REVIEWS AFFECT BOX OFFICE PERFORMANCE?

---

This is the project I worked on for my Master's Thesis.

The central research question was:

> "TO WHAT EXTENT DO REVIEWS INFLUENCE THE BOX OFFICE LEGS OF THEATRICAL MOVIE RELEASES, AND HOW DOES BUZZ INFLUENCE THIS RELATIONSHIP?"

And the goal was to expand on the research into the long-term performance of movies in the box office. It has been a widely debated topic due to the rise of streaming services. Which has caused less traffic towards the cinemas. Therefore, it brings up the question of what can actually improve long-term box office performance.

To narrow down the scope I wanted to focus on the consumer. What factors by the consumer can affect a movie's performance. Since at the end of the day that is the target group. In this case I wanted to focus on the abundance and the sentiment. Abundance as in volume of consumer engagement in the form of a review. And sentiment as in the emotion of consumer engagement. As well as the overall buzz around a movie which signifies the overall engagement.

---

## Preliminary Information

The data cleaning, wrangling, and analysis was mostly performed in Excel and R. To replicate my findings I would suggest using R since all my code is located in R notebooks.

Below I will describe each file to provide context for the purpose of replicating the same findings I got during my research.

### Project Files

| File | Description |
|---|---|
| `Cleaning_Filtered.Rmd` | This is the more limited data cleaning file. By limited I mean that it does not include all of the data cleaning I performed. This is due to the large CSV files that required importing and cleaning which cannot be pushed to Github. For that reason I created this file so that you can still import the final analysis datasets but excluding the cleaning process which involved importing massive CSV files. |
| `Cleaning.Rmd` | This is the original cleaning file that I used for my research. It contains all the steps I took to clean my datasets. |
| `Analysis.Rmd` | This is a notebook with all the analysis I performed on the data. From descriptive analysis to more complex regressions. It also contains the assumption tests I conducted. |
| `Buzz/` | This folder contains Google Trends data for all the movies within my sample. 335 movies to be specific. |
| `movies.csv` | Contains various convenient movie indicators ranging that were used for cleaning and merging. Such as movieId, movieYear and movieTitle. As well as the variable release_date_theaters that was used to calculate box office legs. |
| `revenues_clean.csv` | Contains financial information which was used as a indicator for performance. As well as control variables such as Genre and Season. |
| `critic_analysis_data.csv` | The final critic review analysis dataset. This is the dataset after all the cleaning. The original dataset is too large in file size to be able to be pushed to Github. |
| `user_analysis_data.csv` | The final user review analysis dataset. This is the dataset after all the cleaning. The original dataset is too large in file size to be able to be pushed to Github. |

## How to Replicate Findings?
