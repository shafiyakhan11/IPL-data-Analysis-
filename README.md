# IPL Data Analysis Report

## Project Overview

This project is an **IPL Sports Data Analysis** performed using Python in Google Colab. The main objective is to analyze IPL team and player performance using CSV datasets and derive meaningful insights through data aggregation and visualization.

The analysis focuses primarily on **IPL 2025 batting and bowling statistics**, including runs, matches, batting averages, strike rates, wickets, bowling economy, and other performance indicators.

The project demonstrates the use of Python-based data analysis techniques such as `groupby()`, aggregation, merging datasets, calculated metrics, and graphical visualization.

---

## Objectives

The key objectives of this project are:

* Analyze IPL team performance using player statistics.
* Calculate total runs scored by each team.
* Calculate total wickets taken by each team.
* Compare teams based on runs, matches, and wickets.
* Calculate average runs and wickets per match.
* Explore individual batting and bowling performances.
* Present team comparisons using bar charts.
* Develop practical experience with CSV data and Pandas.

---

## Dataset

The notebook uses two CSV datasets:

### 1. IPL2025Batters.csv

The batting dataset contains **156 rows and 14 columns**.

The main columns include:

| Column      | Description        |
| ----------- | ------------------ |
| Player Name | Name of the player |
| Team        | IPL team           |
| Runs        | Total runs scored  |
| Matches     | Matches played     |
| Inn         | Innings played     |
| No          | Not-out innings    |
| HS          | Highest score      |
| AVG         | Batting average    |
| BF          | Balls faced        |
| SR          | Strike rate        |
| 100s        | Centuries          |
| 50s         | Half-centuries     |
| 4s          | Number of fours    |
| 6s          | Number of sixes    |

The first five players in the dataset include Sai Sudharsan, Surya Kumar Yadav, Virat Kohli, Shubman Gill, and Mitchell Marsh.

### 2. IPL2025Bowlers.csv

The bowling dataset contains **108 rows and 13 columns**.

The main columns include:

| Column      | Description          |
| ----------- | -------------------- |
| Player Name | Name of the player   |
| Team        | IPL team             |
| WKT         | Wickets taken        |
| MAT         | Matches played       |
| INN         | Innings bowled       |
| OVR         | Overs bowled         |
| RUNS        | Runs conceded        |
| BBI         | Best bowling innings |
| AVG         | Bowling average      |
| ECO         | Economy rate         |
| SR          | Bowling strike rate  |
| 4W          | Four-wicket hauls    |
| 5W          | Five-wicket hauls    |

The leading wicket-takers shown in the dataset include Prasidh Krishna, Noor Ahmad, Josh Hazlewood, Trent Boult, and Arshdeep Singh.

---

## Technologies and Libraries

The project is implemented in **Python 3** using Google Colab.

The following libraries are used:

* **Pandas** – data loading, manipulation, grouping, aggregation, and merging.
* **NumPy** – numerical operations.
* **Matplotlib** – creating charts and visualizations.
* **Seaborn** – data visualization.

These libraries are imported at the beginning of the notebook.



## Data Analysis Process

### 1. Loading the Data

The batting dataset is loaded using Pandas:

```python
df = pd.read_csv('IPL2025Batters.csv')
```

Similarly, the bowling dataset is loaded as:

```python
df_2 = pd.read_csv('IPL2025Bowlers.csv')
```

## The notebook displays the datasets and examines their initial records.

## 2. Team-wise Run Analysis

The project groups the batting data by team and calculates total runs:

```python
team_runs = df.groupby('Team')['Runs'].sum().reset_index()
```

The resulting analysis shows that **PBKS has the highest total runs with 3,000**, followed by MI with 2,802 runs and GT with 2,766 runs. KKR has the lowest total among the teams in this analysis, with 1,886 runs.

### Total Runs by Team

| Team |  Runs |
| ---- | ----: |
| PBKS | 3,000 |
| MI   | 2,802 |
| GT   | 2,766 |
| LSG  | 2,598 |
| RCB  | 2,539 |
| RR   | 2,496 |
| DC   | 2,386 |
| SRH  | 2,378 |
| CSK  | 2,315 |
| KKR  | 1,886 |



## 3. Team-wise Match Analysis

The notebook calculates the total number of matches represented by the batting dataset for each team.

PBKS has the highest total at **176 matches**, while SRH has the lowest at **136 matches** among the teams included in the analysis.



## 4. Team-wise Performance Statistics

The run and match datasets are merged to create a combined team statistics table.

The notebook calculates an average using:

```python
team_stats['average'] = team_stats['Runs'] / team_stats['Matches']
```

Based on this calculation, **GT has the highest calculated runs-per-match value at approximately 17.73**, followed by SRH at approximately 17.49. KKR has the lowest value at approximately 13.57.

> Note: This "average" is the notebook's calculated `Runs / Matches` metric and should not be interpreted as the conventional team innings run rate.


## 5. Team-wise Wicket Analysis

The bowling dataset is grouped by team to calculate total wickets:

```python
team_Wickets = df_2.groupby('Team')['WKT'].sum().reset_index()
```

The analysis shows that **MI has the highest total wickets with 109**, followed by PBKS with 95 and RCB with 91. RR has the lowest total with 65 wickets.

### Total Wickets by Team

| Team | Wickets |
| ---- | ------: |
| MI   |     109 |
| PBKS |      95 |
| RCB  |      91 |
| GT   |      87 |
| SRH  |      81 |
| CSK  |      80 |
| KKR  |      78 |
| LSG  |      76 |
| DC   |      67 |
| RR   |      65 |



## 6. Wickets per Match

The notebook combines team wicket totals with match totals and calculates:

```python
team_stats2['average'] = team_stats2['WKT'] / team_stats2['Matches']
```

The highest calculated wickets-per-match value is for **MI at approximately 0.661**, followed by RCB at approximately 0.611 and SRH at approximately 0.596. RR has the lowest value at approximately 0.404.


## 7. Visualizations

The notebook uses Matplotlib to visually compare team performance.

### Total Runs by IPL Teams

A bar chart is created to compare the total runs scored by each team. The visualization makes it easier to identify teams with relatively higher and lower aggregate batting output.

### Total Wickets by IPL Teams

A second bar chart compares the total wickets taken by each IPL team. This visualization highlights MI's leading wicket total and provides a direct comparison across the ten teams.



## Key Findings

Based on the calculations performed in the notebook:

* **PBKS recorded the highest aggregate runs**, with 3,000 runs.
* **MI recorded the second-highest aggregate runs**, with 2,802.
* **GT had the highest calculated runs-per-match metric**, at approximately 17.73.
* **MI recorded the highest number of wickets**, with 109.
* **PBKS recorded 95 wickets**, the second-highest total.
* **RR recorded the lowest total wickets**, with 65.
* **MI had the highest calculated wickets-per-match metric**, at approximately 0.661.
* The batting dataset contains **156 player records**, while the bowling dataset contains **108 player records**.


## Top Batting Performances

The batting data shows several notable individual performances.

The top five records by runs shown in the notebook are:

| Player            | Team | Runs | Average | Strike Rate |
| ----------------- | ---- | ---: | ------: | ----------: |
| Sai Sudharsan     | GT   |  759 |   54.21 |      156.17 |
| Surya Kumar Yadav | MI   |  717 |   65.18 |      167.91 |
| Virat Kohli       | RCB  |  657 |   54.75 |      144.71 |
| Shubman Gill      | GT   |  650 |   50.00 |      155.87 |
| Mitchell Marsh    | LSG  |  627 |   48.23 |      163.70 |

These records also include information about boundaries, half-centuries, centuries, and highest scores.


## Top Bowling Performances

The bowling dataset begins with the following leading wicket-takers:

| Player          | Team | Wickets | Bowling Average | Economy |
| --------------- | ---- | ------: | --------------: | ------: |
| Prasidh Krishna | GT   |      25 |           19.52 |    8.27 |
| Noor Ahmad      | CSK  |      24 |           17.00 |    8.16 |
| Josh Hazlewood  | RCB  |      22 |           17.54 |    8.77 |
| Trent Boult     | MI   |      22 |           23.50 |    8.96 |
| Arshdeep Singh  | PBKS |      21 |           24.66 |    8.88 |

These statistics provide a basis for comparing wicket-taking ability, economy, and bowling efficiency.



## Learning Outcomes

This project provides practical experience in:

* Loading CSV datasets using Pandas.
* Exploring structured sports data.
* Using `groupby()` for team-level analysis.
* Applying aggregation functions.
* Combining datasets using `merge()`.
* Creating calculated performance metrics.
* Working with numerical and categorical data.
* Creating bar charts with Matplotlib.
* Communicating analytical results through data visualization.

The original notebook specifically identifies `groupby` and aggregate functions, large CSV handling, and visualization storytelling as key learning outcomes.


## Conclusion

This IPL data analysis project demonstrates how Python can be used to analyze real-world sports statistics. The notebook combines batting and bowling datasets to compare IPL teams on aggregate runs, matches, wickets, and calculated performance measures.

The analysis identifies **PBKS as the team with the highest aggregate runs in the dataset and MI as the team with the highest aggregate wickets**. It also demonstrates how grouping, aggregation, merging, calculated metrics, and visualization can transform raw player-level data into useful team-level insights.

Overall, the project provides a practical introduction to **exploratory data analysis and sports analytics using Python and Pandas**.


## Future Scope

The project could be extended by adding:

* Player-wise batting and bowling rankings.
* Comparison of batting strike rates and bowling economy rates.
* Correlation analysis between batting and bowling metrics.
* Interactive dashboards.
* Team-wise performance comparisons using multiple metrics.
* Advanced statistical analysis.
* Machine learning models for predicting player or team performance.


## Project Files

```text
IPL Data Analysis
│
├── iplDataAnalysisReport.ipynb
├── IPL2025Batters.csv
└── IPL2025Bowlers.csv
```

## How to Run

1. Open the notebook in Google Colab.
2. Upload `IPL2025Batters.csv` and `IPL2025Bowlers.csv`.
3. Run the cells sequentially.
4. Review the generated tables and visualizations.
5. Modify the analysis or add additional metrics as required.



## Author

**Shafiya khan**

**Project:** IPL Data Analysis
**Platform:** Google Colab
**Language:** Python
**Libraries:** Pandas, NumPy, Matplotlib, Seaborn
