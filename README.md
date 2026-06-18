# 🎬 Analysis of Pixar Films

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-orange)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4c8cbf)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)

---

## Overview

This project is a comprehensive exploratory data analysis (EDA) of Pixar films — examining their release history, box office performance, critical and audience reception, genre composition, Academy Award nominations, and the people behind the films. The analysis spans 28 Pixar films across six interconnected datasets, uncovering patterns in financial performance, creative contributions, and critical acclaim.

---

## Business Problem

Pixar Animation Studios has produced a rich catalog of films over several decades. Despite their cultural and commercial impact, there is limited structured analysis that connects film-level attributes — such as runtime, genre, budget, and ratings — with commercial outcomes and award recognition. Understanding these relationships can help contextualize Pixar's success and inform decisions in content strategy, marketing, and production planning.

---

## Business Objective

The objective of this analysis is to explore and surface meaningful insights from Pixar's film portfolio by investigating:

- Historical release trends and audience targeting (ratings and runtime)
- Genre popularity and subgenre classifications across the catalog
- Box office performance and return on investment (ROI) by film
- Critical consensus and audience reception across Rotten Tomatoes, Metacritic, and IMDb
- Academy Award nomination and win patterns
- Key contributors (directors, producers, writers, composers) and their involvement across multiple films

---

## Dataset

### Source
The dataset was sourced from the **Maven Analytics Data Playground**:
[https://mavenanalytics.io/data-playground](https://mavenanalytics.io/data-playground?dataStructure=Multiple%20tables&order=date_added%2Cdesc)

### Dataset Summary

The project uses **6 CSV files** representing different dimensions of the Pixar film catalog:

| File | Description |
|---|---|
| `pixar_films.csv` | Film titles, release dates, runtimes, and film ratings |
| `pixar_people.csv` | Names and role types of key contributors per film |
| `genres.csv` | Genre and subgenre classifications per film |
| `box_office.csv` | Budget and box office earnings (US/Canada, international, worldwide) |
| `public_response.csv` | Rotten Tomatoes, Metacritic, IMDb scores, CinemaScore ratings |
| `academy.csv` | Academy Award nominations, wins, and eligibility statuses |

### Dataset Challenges

- **Missing budget data**: The film *Luca* had no budget value and was excluded from ROI and budget-related analyses. It was replaced with 0 for general summary calculations.
- **Missing CinemaScore data**: Three films (*Soul*, *Luca*, *Turning Red*) had no CinemaScore entry, filled with "Unknown".
- **Duplicate records**: The `pixar_people.csv` dataset contained duplicate rows, which were identified and removed before analysis.
- **Data type corrections**: The `release_date` column required conversion from object to `datetime`, and box office earnings columns required conversion from integer to `float`.

---

## Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3.x |
| Data Manipulation | Pandas, NumPy |
| Data Visualization | Matplotlib, Seaborn |
| Environment | Jupyter Notebook |
| Data Source | Maven Analytics Data Playground |

---

## Project Workflow

1. **Data Collection and Loading** — Loaded 6 CSV files into individual DataFrames
2. **Data Exploration** — Inspected shape, data types, missing values, and duplicates for each dataset
3. **Data Cleaning** — Corrected data types, handled missing values, and removed duplicate rows
4. **Exploratory Data Analysis** — Investigated key questions across all 6 datasets using aggregations and visualizations

---

## Exploratory Data Analysis

The EDA was structured around six datasets, each with targeted analytical questions:

### 1. Films Data
- Pixar's catalog spans **28 distinct films**, with *Toy Story* (1995) being the oldest and the most recent release captured in the dataset
- Films were primarily released in two eras: 2000–2010 (10 films) and 2011–2020 (10 films), with 5 films released before 2000 and 3 after 2020
- Runtime ranges from the shortest to the longest film, with an average runtime of **100 minutes**
- All films carry one of two MPAA ratings — **G** or **PG** — with the majority rated PG; the last G-rated Pixar film was *Bear Story* (2017)
- **Friday** is by far the most common release day, accounting for approximately **93%** of all Pixar film releases

### 2. Film-makers Data
- Six core role types contribute to each film: **Director, Co-Director, Producer, Screenwriter, Musician,** and **Story**
- **Andrew Stanton** is the most prolific contributor, involved in 20 films across multiple roles, followed by **Pete Docter** (14 films) and **John Lasseter** (13 films)
- Several contributors held both directing and producing roles across different films
- Some films had multiple people serving the same role (e.g., co-directors, multiple producers)

### 3. Genres Data
- Every film is assigned exactly **3 genre tags** and at least 1 subgenre
- **Adventure** and **Animation** are the two most common genres, each appearing in 28 films; **Comedy** follows with 21 appearances
- **WALL-E**, **Cars 2**, and **Brave** each have the highest number of subgenre classifications at **6 subgenres** each
- The top 5 subgenres include categories such as **Buddy, Road Trip, Slapstick, Parody**, and **Superhero**

### 4. Box Office Data
- Total estimated budget across all films is approximately **$3.6 billion**, with an average budget of ~**$130 million** per film
- The most expensive films had budgets of **$200 million** each; the lowest-budget film (excluding *Luca*) was *Toy Story* at **$30 million**
- Total worldwide box office revenue: **~$16.95 billion** — US/Canada contributed **~$7.29 billion** and international markets **~$9.67 billion**
- Approximately **64%** of films generated a global ROI exceeding 100% of their initial budget
- A minority of films incurred a financial loss

### 5. Public Reviews Data
- **Rotten Tomatoes** scores range from a low to 100, with an average of ~**89**; **Metacritic** averages ~**79**; **IMDb** averages ~**7.7**
- **2 films** received a perfect Rotten Tomatoes score of 100
- Strong positive correlation (**0.82**) exists between Rotten Tomatoes and IMDb scores, and similarly between Rotten Tomatoes and Metacritic scores
- Films scoring above 8.0 on IMDb often exceed **800,000 reviews**, while lower-rated films cluster below 250,000 reviews
- Critics tended to rate more films higher than audiences did (based on IMDb vs. Metacritic comparison)
- Films with an **A+ CinemaScore** had higher average IMDb and Rotten Tomatoes scores compared to those rated A or A−, but not necessarily higher Metacritic scores

### 6. Academy Awards Data
- Pixar films have been considered across multiple award types including **Best Animated Feature, Original Score, Original Screenplay, Adapted Screenplay**, and others
- The majority of records reflect **Nominated** status, with a subset resulting in wins
- Only **1 film** was nominated in the **Adapted Screenplay** category (*Toy Story 3*)
- Some films have award types marked **"Award not yet introduced"**, reflecting the historical absence of certain categories
- A handful of films were marked **Ineligible** for specific award categories

---

## Key Findings

- **Friday dominates as Pixar's release day** — 93% of films were released on Fridays, a deliberate strategy to maximize opening weekend performance.
- **Adventure and Animation are Pixar's genre pillars** — both appear across all 28 films, reinforcing the studio's creative identity.
- **International markets outperform domestic** — nearly 57% of worldwide revenue came from outside the US and Canada, underscoring Pixar's global brand strength.
- **The majority of Pixar films are highly profitable** — 64% returned more than 100% of their budget through worldwide box office alone.
- **Critics and audiences largely agree** — a 0.82 correlation between Rotten Tomatoes and IMDb scores suggests strong consensus across critic and audience platforms.
- **A small group of contributors power the catalog** — Andrew Stanton, Pete Docter, and John Lasseter collectively contributed to over 40 films worth of involvement, forming the creative backbone of the studio.
- **Every film carries both genre and subgenre tags** — there are no films with genre-only or subgenre-only classifications, suggesting a consistent tagging discipline in the dataset.

---

## Business Impact

The findings from this analysis offer several practical takeaways for entertainment industry stakeholders:

- **Release scheduling**: The Friday release preference is well-supported by the data. Studios can use this benchmark when planning theatrical release calendars for animated features.
- **Budget benchmarking**: With an average budget of ~$130M and the majority of films exceeding 100% ROI, Pixar's financial model serves as a benchmark for premium animated content investment.
- **Global content strategy**: The dominance of international revenue suggests that studios should prioritize global marketing and localization efforts, not just domestic campaigns.
- **Talent pipeline**: The concentration of creative output among a small group of veteran contributors highlights the importance of retaining and developing core creative talent.
- **Critical-audience alignment**: The high correlation across review platforms indicates that Pixar films consistently satisfy both critics and audiences, a rare combination that supports long-term brand equity.

---

## Repository Structure

```
pixar-films-analysis/
│
├── Analysis_of_Pixar_Films.ipynb   # Main Jupyter Notebook with full EDA
├── pixar_films.csv                  # Films dataset
├── pixar_people.csv                 # Film-makers dataset
├── genres.csv                       # Genres dataset
├── box_office.csv                   # Box office dataset
├── public_response.csv              # Public reviews dataset
├── academy.csv                      # Academy Awards dataset
└── README.md                        # Project documentation
```

---

## Author

**Reemika Subrata Das**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-reemikadas-0077B5?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/reemikadas)
[![GitHub](https://img.shields.io/badge/GitHub-reemikadas-181717?style=flat&logo=github&logoColor=white)](https://github.com/reemikadas)
[![Email](https://img.shields.io/badge/Email-das.reemika%40gmail.com-D14836?style=flat&logo=gmail&logoColor=white)](mailto:das.reemika@gmail.com)
