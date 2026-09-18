# Experiment 1: IPL Dataset – Data Cleaning and Exploratory Data Analysis (EDA)

## Aim

To perform Exploratory Data Analysis (EDA) on the IPL matches dataset by cleaning the data, analyzing matches played per season, identifying top winning teams, studying toss decisions, exploring venue statistics, and deriving meaningful insights using Python.

---

## Algorithm / Procedure

### 1. Import Libraries

* Import **Pandas** for data manipulation and analysis.
* Import **Matplotlib** for data visualization.

### 2. Load Dataset

* Load the IPL matches dataset using `pd.read_csv()`.
* Display the dataset dimensions using `.shape`.
* View the first five records using `.head()`.
* Check column names and data types.

### 3. Data Cleaning

* Identify missing values using `.isnull().sum()`.
* Fill missing values in the **city** column with `"Unknown"`.
* Check and remove duplicate records using `.drop_duplicates()`.

### 4. Matches per Season (GroupBy Analysis)

* Group the dataset by **season**.
* Count the number of matches played in each season.
* Display the season with the highest number of matches.
* Plot a bar chart for visualization.

### 5. Team Performance Analysis

* Group the dataset by the **winner** column.
* Count total wins for each team.
* Display the top five winning teams.
* Visualize the results using a bar chart.

### 6. Filtering

* Filter all matches won by **Chennai Super Kings**.
* Display the season, participating teams, and match winner.

### 7. Toss Decision Analysis

* Count the frequency of **Bat** and **Field** decisions.
* Calculate the percentage of each toss decision.
* Display the results using a bar chart.

### 8. Cross-Tabulation

* Create a season-wise comparison of toss decisions using `pd.crosstab()`.
* Identify the most preferred toss decision for each season.

### 9. Venue Analysis

* Count the number of matches conducted at each venue.
* Display the top five venues hosting the maximum number of IPL matches.

### 10. Winning Margin Analysis

* Find the largest winning margin in IPL history.
* Display the top ten matches with the highest winning margins.

### 11. Data Transformation

* Convert the **date** column into DateTime format.
* Create a new **Year** column.
* Create a **Win Type** column based on the match result.

### 12. Save the Cleaned Dataset

* Save the processed dataset as **IPL_Matches_Cleaned.csv**.

---

## Program

```
Experiment -1
Developed by : Niranjani.C
Registration number : 212223220069

import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv("matches.csv")
print("Dataset Loaded Successfully!")

df.head()

print("Rows :", df.shape[0])
print("Columns :", df.shape[1])

df.columns

df.dtypes

print(df["id"].is_unique)

df.isnull().sum()

df.duplicated().sum()

df["city"] = df["city"].fillna("Unknown")
df = df.drop_duplicates()
matches_per_season = df.groupby("season").size()
matches_per_season

matches_per_season.plot(kind="bar", figsize=(10,5))
plt.title("IPL Matches Per Season")
plt.xlabel("Season")
plt.ylabel("Matches")
plt.xticks(rotation=45)
plt.show()

team_wins = df.groupby("winner").size().sort_values(ascending=False)
team_wins

top5 = team_wins.head()
top5

top5.plot(kind="bar", figsize=(8,5))
plt.title("Top 5 Winning Teams")
plt.show()

csk = df[df["winner"]=="Chennai Super Kings"]
csk.head()

df["toss_decision"].value_counts()

df["toss_decision"].value_counts().plot(kind="bar")
plt.show()

pd.crosstab(df["season"],df["toss_decision"])

df.groupby("venue").size().sort_values(ascending=False).head()

df["result_margin"].max()

df["date"] = pd.to_datetime(df["date"])
df["year"] = df["date"].dt.year
df[["date","year"]].head()

df["win_type"] = df["result"].replace({
    "runs":"Won by Runs",
    "wickets":"Won by Wickets",
    "tie":"Tie",
    "no result":"No Result"
})
df.head()

df.to_csv("IPL_Matches_Cleaned.csv", index=False)
print("Saved Successfully")


```

---

## Output

<img width="946" height="851" alt="image" src="https://github.com/user-attachments/assets/ba4688e1-fe28-4881-a7b2-f4cb53e16040" />
<img width="951" height="582" alt="image" src="https://github.com/user-attachments/assets/7a6bc13f-2b51-4e31-9fb1-b48af25fae9e" />
<img width="942" height="590" alt="image" src="https://github.com/user-attachments/assets/a856c75a-f4db-4e84-b172-084f435a0501" />
<img width="956" height="771" alt="image" src="https://github.com/user-attachments/assets/3de0b03a-5d3f-4adf-8c9e-10350f97b1a0" />
<img width="947" height="858" alt="image" src="https://github.com/user-attachments/assets/ab5f7f90-054b-43bb-a5e0-5bd928b498a8" />
<img width="967" height="858" alt="image" src="https://github.com/user-attachments/assets/1955323c-45ec-4112-90d5-571f1af2b2b8" />
<img width="965" height="595" alt="image" src="https://github.com/user-attachments/assets/37241b45-9d16-4402-a095-0cc423cd586d" />
<img width="948" height="441" alt="image" src="https://github.com/user-attachments/assets/6535ff73-1c87-4c4b-9c5f-cbddcb810c6d" />
<img width="852" height="77" alt="image" src="https://github.com/user-attachments/assets/5f26b466-1f73-4e2d-80a2-22387fcbc361" />
<img width="782" height="230" alt="image" src="https://github.com/user-attachments/assets/d534a758-c566-4df7-ab0c-ac861febffa3" />
<img width="940" height="823" alt="image" src="https://github.com/user-attachments/assets/55fa4003-ddf5-43f1-bdba-e3180a6f82cd" />


---

## Result

The experiment was executed successfully. The IPL dataset was cleaned and analyzed using Exploratory Data Analysis techniques. Insights regarding seasonal matches, team performance, toss decisions, winning margins, and venue statistics were obtained successfully.

---


