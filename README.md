
# DO REVIEWS AFFECT BOX OFFICE PERFORMANCE?

---

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

---

## Preliminary Information

The data cleaning, wrangling, transformation, and statistical analysis for this project were primarily performed using **R** and **Microsoft Excel**.

For replication purposes, I recommend using **R / RStudio**, as the reproducible portions of the data-processing and analysis workflow are contained in the R Markdown (`.Rmd`) notebooks in this repository.

The project contains two different cleaning notebooks.

`Cleaning.Rmd` represents the original data-cleaning workflow used during the thesis. However, some of the original review datasets were too large to upload to GitHub.

For this reason, `Cleaning_Filtered.Rmd` provides a more practical starting point for anyone interested in reproducing the analysis using the cleaned datasets available in this repository.

The intended replication workflow is therefore:

**Cleaned Data → Cleaning_Filtered.Rmd → Analysis.Rmd → Statistical Results**

Users who have access to the original raw datasets can instead follow the complete workflow contained in `Cleaning.Rmd`.

---

### Project Files

| File | Description |
|---|---|
| `Cleaning_Filtered.Rmd` | A simplified and reproducible version of the data-cleaning workflow. The original Rotten Tomatoes review files were too large to upload to GitHub, so this notebook begins from the cleaned analysis datasets included in this repository. This is the recommended starting point for most users. |
| `Cleaning.Rmd` | The original cleaning notebook used during the thesis. It documents the broader data-processing procedure, including the steps used to process and merge the original datasets. Some source files required by this notebook are not included in the repository because of GitHub file-size limitations. |
| `Analysis.Rmd` | The primary statistical-analysis notebook. It contains descriptive statistics, visualizations, Pearson correlation analyses, regression models, moderation analyses, transformations, and model-assumption testing used in the thesis. |
| `Buzz/` | Contains the Google Trends search-interest data collected for the movies in the final sample. Google Trends data was collected individually for the films and later merged with the review and financial datasets. |
| `movies.csv` | Contains general movie-level identifiers and variables used during cleaning and merging, including variables such as movie ID, title, year, and theatrical release date. The theatrical release date was also used when determining the relevant review window. |
| `revenues_clean.csv` | Contains the financial and movie-level information used in the analysis. This includes the revenue variables required to calculate box office legs as well as control variables such as genre, release season, and production budget. |
| `critic_analysis_data.csv` | The final cleaned critic-review dataset used for the analysis. The original critic-review source dataset was considerably larger and is therefore not stored directly in this repository. |
| `user_analysis_data.csv` | The final cleaned user-review dataset used for the analysis. As with the critic data, the original source dataset was too large to include directly in the repository. |

---

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

Critic and user review data originated from a publicly available **Rotten Tomatoes dataset hosted on Kaggle**.

The original dataset contains a very large number of individual reviews and therefore could not be included in full in this repository.

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

---

## Variable Construction

The main variables used in the project are summarized below.

### Box Office Legs

Box office legs represent the dependent variable of this study and were calculated as:

```text
Box Office Legs = Total Domestic Gross / Opening Weekend Gross
