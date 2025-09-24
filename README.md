# Programming Assignment 4 – Data Wrangling and Data Visualization

**Author:** ESMENDA, Francine Jasmine Guelle T. 

**Course:** Advanced Computer Programming and Algorithms / ECE2112  

---

## Description  

This Jupyter Notebook demonstrates **data wrangling and data visualization** techniques using **Pandas, Matplotlib, and Seaborn**.  

The problems solved include:    
1. **Data Wrangling** – Filtering the dataset to create specific DataFrames based on conditions.  
2. **Data Visualization** – Using bar plots to show how different features (track, gender, hometown) affect average scores.  

---

## Examples w/ Explanation
**Problem 1**

```python
#import pandas library for data analysis
import pandas as pd

#Load the Excel sheet into a DataFrame
data = pd.read_excel("board2.xlsx", sheet_name="board2.csv")
```
- Loads the Excel dataset into a Pandas DataFrame named data.

```python
#Filter Visayas students with Math < 70 and show selected columns
Vis = data[(data["Hometown"] == "Visayas") & (data["Math"] < 70)][["Name", "Gender", "Track", "Math"]]
```
- Filters students from Visayas with Math scores less than 70.
- Displays only the columns: Name, Gender, Track, and Math.

```python
#Filter Instrumentation students from Luzon with Electronics > 70
Instru = data[(data["Track"] == "Instrumentation") & 
              (data["Hometown"] == "Luzon") & 
              (data["Electronics"] > 70)][["Name", "GEAS", "Electronics"]]
```
- Filters students where:
    - Track = Instrumentation
    - Hometown = Luzon
    - Electronics > 70
- Shows Name, GEAS, and Electronics columns.

```python
#Compute Average score across all subjects
data["Average"] = data[["Math", "Electronics", "GEAS", "Communication"]].mean(axis=1)

#Filter Female students from Mindanao with Average >= 55
Mindy = data[(data["Hometown"] == "Mindanao") & 
             (data["Gender"] == "Female") & 
             (data["Average"] >= 55)][["Name", "Track", "Electronics", "Average"]]
```
- Creates a new column Average = mean of Math, Electronics, GEAS, and Communication.
- Filters female students from Mindanao with an average score ≥ 55.

```python
#Print results
print("Vis DataFrame:\n", Vis, "\n")
print("Instru DataFrame:\n", Instru, "\n")
print("Mindy DataFrame:\n", Mindy, "\n")
```
- Displays the three filtered DataFrames (Vis, Instru, Mindy) for checking.

---

**Problem 2**

```python
import matplotlib.pyplot as plt
import seaborn as sns
```
- matplotlib and seaborn are used for plotting graphs.
  
```python
#By Track
sns.barplot(x="Track", y="Average", data=data, errorbar=None)
plt.title("Average Score by Track")
plt.show()
```
- Groups by Track and shows average performance.
- Helps compare how different college tracks perform.

```python
#By Gender
sns.barplot(x="Gender", y="Average", data=data, errorbar=None)
plt.title("Average Score by Gender")
plt.show()
```
- Groups by Gender (Male/Female).
- Shows if gender affects student averages.

```python
#By Hometown
sns.barplot(x="Hometown", y="Average", data=data, errorbar=None)
plt.title("Average Score by Hometown")
plt.show()
```
- Groups by Hometown (Luzon, Visayas, Mindanao).
- Shows how region affects exam averages.

---
### Version History
v1.0 – Loaded dataset and created base DataFrame.

v1.1 – Implemented filters for Vis, Instru, Mindy.

v1.2 – Added "Average" computation.

v1.3 – Created bar plots by Track, Gender, and Hometown.

---


