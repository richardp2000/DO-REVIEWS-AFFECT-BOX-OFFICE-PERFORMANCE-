# DO REVIEWS AFFECT BOX OFFICE PERFORMANCE?

------------------------------------------------------------------------

This repository contains the research project I completed for my Master's Thesis in Marketing.

The thesis is titled:

> **"THE IMPACT OF REVIEWS AND ONLINE BUZZ ON LONG-TERM BOX OFFICE PERFORMANCE"**

The central research question was:

> **"To what extent do reviews influence the box office legs of theatrical movie releases and how does buzz influence this relationship?"**

The goal of this research was to expand the existing literature on movie box office performance by looking beyond traditional measures such as opening-weekend revenue, weekly revenue, or total box office revenue.

Instead, this study focuses on **long-term theatrical performance**, measured through a concept known as **box office legs**.

A movie has strong box office legs when it continues to generate revenue after its opening weekend rather than experiencing a heavily front-loaded theatrical run.

To narrow the scope of the research, I focused primarily on consumer-related factors that may influence this sustained performance. More specifically, I examined three aspects of audience engagement:

- **Review Volume** — the number of reviews a movie receives.
- **Review Valence** — the proportion of those reviews that are positive.
- **Online Buzz** — the level of general consumer attention surrounding a movie, measured using Google Trends search interest.

Reviews were further separated into:

- **Critic Reviews**
- **User Reviews**

This allowed me to investigate whether professional critics and general moviegoers have different relationships with a movie's long-term theatrical performance.

An additional objective of the research was to separate **buzz** from traditional electronic word-of-mouth. Reviews contain an evaluative component, whether people liked or disliked a movie. Whereas buzz captures the broader attention and interest surrounding a movie.

The final study consists of **335 theatrical movie releases in the United States between 2004 and 2024**.

------------------------------------------------------------------------

## Preliminary Information

The data cleaning, wrangling, transformation, and statistical analysis for this project were primarily performed using **R** and **Microsoft Excel**.

For replication purposes, I recommend using **R / RStudio**, as the reproducible portions of the data-processing and analysis workflow are contained in the R Markdown (`.Rmd`) notebooks in this repository.

The project contains an original cleaning notebook.

`Cleaning.Rmd` represents the original data-cleaning workflow used during the thesis. However, some of the original review datasets were too large to upload to GitHub.

For this reason, `Import_Cleaned_Data.Rmd` provides a more practical starting point for anyone interested in reproducing the analysis results using the cleaned datasets available in this repository.

The intended replication workflow is therefore:

**Import_Cleaned_Data.Rmd → Analysis.Rmd**

Users who have access to the original raw datasets can instead follow the complete workflow contained in `Cleaning.Rmd`.

------------------------------------------------------------------------

### Project Files

| File | Description |
|------------------------------------|------------------------------------|
| `Import_Cleaned_Data.Rmd` | A notebook to import the final cleaned datasets without the cleaning portion. The original Rotten Tomatoes review files were too large to upload to GitHub, for that reason I exported the final datasets as a CSV to be imported in this notebook. This is the recommended starting point for most users. |
| `Cleaning.Rmd` | The original cleaning notebook used during the thesis. It documents the broader data-processing procedure, including the steps used to process and merge the original datasets. Some source files required by this notebook are not included in the repository because of GitHub file-size limitations. |
| `Analysis.Rmd` | The primary statistical-analysis notebook. It contains descriptive statistics, visualizations, Pearson correlation analyses, regression models, moderation analyses, transformations, and model-assumption testing used in the thesis. |
| `Buzz/` | Contains the Google Trends search-interest data collected for the movies in the final sample. Google Trends data was collected individually for the films and later merged with the review and financial datasets. |
| `movies.csv` | Contains general movie-level identifiers and variables used during cleaning and merging, including variables such as movie ID, title, year, and theatrical release date. The theatrical release date was also used when determining the relevant review window. |
| `revenues_clean.csv` | Contains the financial and movie-level information used in the analysis. This includes the revenue variables required to calculate box office legs as well as control variables such as genre, release season, and production budget. |
| `critic_analysis_data.csv` | The final cleaned critic-review dataset used for the analysis. The original critic-review source dataset was considerably larger and is therefore not stored directly in this repository. |
| `user_analysis_data.csv` | The final cleaned user-review dataset used for the analysis. As with the critic data, the original source dataset was too large to include directly in the repository. |

------------------------------------------------------------------------

## Data Sources

The project combines secondary data from multiple sources.

### Box Office Data

Movie-level box office information was collected from **Box Office Mojo**.

The main financial variables used were:

- Opening-weekend domestic gross
- Total domestic box office gross

These variables were used to calculate the dependent variable, **box office legs**.

Additional information on the length of a film's theatrical run was obtained from **The Numbers**. This was used to determine the time period during which reviews could reasonably have affected theatrical performance.

### Review Data

Critic and user review data originated from a publicly available **Rotten Tomatoes** dataset hosted on **Kaggle**.

The original dataset contains a very large number of individual reviews and therefore could not be included in full in this repository due to the file size limit.

The analysis distinguishes between:

- Professional critic reviews
- User-generated reviews

Only reviews published during each movie's theatrical run were retained for the final analysis.

### Buzz Data

Online buzz was measured using **Google Trends**.

For each movie, search interest was collected using the movie title as the search term.

No additional terms such as `"review"` were included because the intention was to capture **general interest in the movie**, rather than review-seeking behaviour specifically.

A consistent **five-week window** was collected for every movie:

- 1 week before theatrical release
- 4 weeks after theatrical release

The daily Google Trends values were averaged across this period to create the variable used in the analysis.

------------------------------------------------------------------------

## Variable Construction

The main variables used in the project are summarized below. Review measures are calculated separately for critic and user reviews, with each resulting dataset containing one observation per movie.

### Box Office Legs (DV)

Box office legs are the continuous dependent variable used to measure a movie's theatrical performance relative to its opening weekend. Higher values indicate that a movie earned more over its full theatrical run relative to its initial earnings.

For example, box office legs of 3.0 mean that total domestic earnings were three times the opening weekend earnings.

`Box Office Legs = Total Domestic Gross / Opening Weekend Gross`

### Review Volume (IV)

Review volume is a discrete, count-based independent variable representing the amount of review activity surrounding a movie. It measures how many reviews were recorded, regardless of whether those reviews were positive or negative.

Review volume is calculated separately for critics and users, using only reviews published within each movie's theatrical window.

`Review Volume = Number of Reviews Within the Theatrical Window`

### Review Valence (IV)

Review valence is a numerical proportion used as an independent variable to represent how positively a movie was evaluated. It ranges from 0 to 1, where higher values indicate a greater share of positive reviews.

For example, a review valence of 0.80 means that 80% of the included reviews were positive. The measure is calculated separately for critic and user reviews.

`Review Valence = Positive Reviews / Total Reviews`

#### Critic Review Valence

Critic review valence uses the existing positive and negative classifications stored in the Rotten Tomatoes dataset's `scoreSentiment` variable. These are categorical sentiment labels rather than numerical ratings.

The labels are standardized by removing surrounding whitespace and converting them to uppercase. The number of positive critic reviews is then divided by the total number of critic reviews within the theatrical window.

#### User Review Valence

User review valence is constructed from the numerical `score` variable. Each rating is converted into a categorical `scoreSentiment` label using the following threshold:

- `score < 3.0 → NEGATIVE`
- `score >= 3.0 → POSITIVE`

The number of positive user reviews is then divided by the total number of user reviews within the theatrical window.

### Average Buzz (Moderator)

Average buzz is a continuous moderator representing online attention surrounding a movie, measured through Google Trends search interest. It is used to examine whether the relationships between review measures and box office legs vary depending on the level of search interest.

Daily search-interest values are averaged across the collected five-week period: one week before theatrical release and four weeks after release. Missing values are excluded from the calculation.

`Average Buzz = Mean of Available Daily Search-Interest Values`


### Variable Transformations

Box office legs and review volume also have log-transformed versions to address right-skewness and reduce the influence of very large values. These are calculated using `log1p(x)`, equivalent to the natural logarithm of one plus the original value.

`Transformed Variable = ln(1 + Original Variable)`

For interaction models, log-transformed review volume, review valence, and average buzz are mean-centered separately within each analysis dataset. This makes zero represent the dataset's average value and helps interpret model coefficients when the interacting variables are at their means.

`Centered Variable = Variable − Mean of the Variable`
