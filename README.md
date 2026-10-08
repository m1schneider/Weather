# Rainfall Comparison between Seattle and Philadelphia

## Overview

The purpose of this project is to analyze rainfall data for Seattle and Philadelphia to answer the following questions: Which city receives more rainfall per year, and which city has a higher proportion of rainy days per year?

---
## Data

The data analyzed in this project was sourced from the National Oceanic and Atmospheric Administration (NOAA) through the NOAA Climate Data Online (CDO) portal. The data is from two weather stations, one in Seattle and one in Philadelphia. The data spans a total of five years, from January 1, 2018, to December 31, 2022.
The data can also be accessed through the following link:
https://www.ncei.noaa.gov/cdo-web/


---

## Project Structure

```
├── data/                 # Raw and processed data
├── code/                 # Jupyter notebooks
├── reports/              # Generated reports and visualizations
├── requirements.txt      # Dependencies
└── README.md             # Project documentation
```




---

## Analysis
The data for this project was gathered by NOAA, however, it had to be appropriately cleaned and organized for analysis. The data that we used was the precipitation data gathered by the two weather stations, and the data was stripped of non-relevant data and reorganized into a long format. This data was then visualized and aggregated to find underlying patterns regarding the precipitation data in terms of rainfall per year and the proportion of days with rainfall. On days of the year where rainfall data was missing, the mean rainfall was added in its place.


The following is a section of the groupby statement that was able to return data on which cities where receiving more rainfall and at what times of the year. The first statement returns the average daily rainfall for both Seattle and Philadelphia, and the seconf statement return the average daily rainfall by month. The monthly breakdown allows us to see the annual trends that both cities experience and how they vary from one another.

```python
df[['city','precipitation']].groupby('city').mean()
```

```python
df[['month', 'precipitation', 'city']].groupby(['month','city']).mean()
```

Visualizing this data also allows us to see the annual trends on a month to month basis to get a better understanding of how both cities varied from on another. The code sections below visualized this data in the form of barplots. The first sections returns a barplot of the mean rainfall per month and the second section returns the proportion of days with rain by month. 

```python
plt.figure(figsize=(20,4))

sns.barplot(data=df, x='month', y='precipitation', hue='city')

plt.xlabel('Month', fontsize=15)
plt.ylabel('Precipitation (inches)', fontsize=15)
plt.tick_params(labelsize=15)
plt.xticks(ticks=range(12), labels=month_names)

plt.show()
```

```python
plt.figure(figsize=(20,4))

sns.barplot(data=df, x='month', y='any_precipitation', hue='city')

plt.xlabel(None)
plt.ylabel('Proportion days with precipitation', fontsize=13)
plt.xticks(ticks=range(12), labels=month_names)
plt.tick_params(labelsize=15)

plt.show()
```


---
## Results
Seattle and Philadelphia were the focus locations of this project, and the key questions that were answered were which city sees more annual rainfall in terms of inches and which city sees a higher proportion of rainy days throughout the year.
In terms of mean annual rainfall, Philadelphia averaged 18.5% more rain throughout the year. In terms of the proportion of days with rain, on the other hand, Seattle averaged 52.4% more days with rain throughout the year when compared to Philadelphia. These figures are yearly averages, and monthly totals varied considerably.


---
## Author
Michael Schneider


---
## License
This repository contains coursework for DATA 5100 at Seattle University. It is shared for portfolio and reference purposes only. Please do not copy or submit it as your own work for academic credit.