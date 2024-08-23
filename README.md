# Weather Data Analysis- CFG Final Project☁️

![Example Image](https://github.com/shravya-nallamilli/CFG-data-project/blob/024d9bcc351b00ce6c2ce8d203f8b07177dcfb77/GirlsWhoCode.jpeg)

**Welcome to our project**!

Team: Shravya Nallamilli, Brenda Org & Louise Smith

## Introduction

This project involves analysing weather data for three UK locations (London, Swansea, and Preston) over the years 2016 to 2024. 

## Objective
The main objective of this project was to analyse historical weather data to identify and compare trends in temperature and precipitation across three UK locations: London, Swansea, and Preston.

## Project folder structure

Explore and visualise data with Python! In this project, we load, clean, and analyse datasets, then create informative visualisations to uncover insights and trends hidden within the data. All the source code is located in the folder named `CFG-data-project`. This code can be run as a standard Jupyter notebook. The folder also contains graphs and data visualisations for three locations: London, Swansea, and Preston. Additionally, a precipitation graph is included to provide a clear visualisation of rainfall amounts.

## Steps for running the code

1. **Clone the git repo locally**:

2. **Install the necessary Libraries**:

 Necessary libraries such as `pandas`, `numpy`, and `matplotlib` are imported, and the `meteostat` package is used to fetch historical weather data.
   
   ```python
   !pip install meteostat
   import pandas as pd
   import numpy as np
   import matplotlib.pyplot as plt
   from datetime import datetime
   from meteostat import Point, Monthly
```
Open `CFG-data-project` in jupyter notebook

Run the Code (It's that simple! 😊)

## Data Source
The weather data used in this project was sourced from the [Meteostat](https://meteostat.net/) library, which offers historical weather and climate data from various locations.

## Results

The graphs represent weather data from three UK locations (London, Swansea, and Preston) over the years 2016 to 2024. The data includes maximum and average temperatures, helping to compare the climate patterns across these locations.

**1. Average Temperature Graphs (First Image)**
- **Purpose:** These graphs compare the average temperatures for London, Swansea, and Preston separately.

**Interpretation:** 

- **London (Green Line)**: Average temperatures range from about 7-20°C, with clear seasonal fluctuations.
- **Swansea (Red Line)**: Shows similar patterns but with slightly lower average temperatures.
- **Preston (Blue Line)**: Lowest average temperatures, around 5-18°C

Key Observation: London generally has higher average temperatures compared to Swansea and Preston.

**2.  Maximum Temperature Graphs (Second Image)**
   - **Purpose**: This set of graphs compares the maximum temperatures for London, Swansea, and Preston separately.

 **Interpretation:**

- **London (Green Line)**: London shows a noticeable cyclical pattern of maximum temperatures, peaking around 22-24°C each summer. The dips likely represent the winter months.
- **Swansea (, Red Line**): Swansea's maximum temperatures are somewhat erratic but generally follow a similar cyclical pattern, with peaks reaching around 20-22°C. 
- **Preston (Blue Line)**: Preston shows lower maximum temperatures compared to London and Swansea, with peaks typically around 18-20°C.

Key Observations: London tends to have the highest maximum temperatures overall, with Preston being cooler on average.

**3. Combined Maximum Temperature Graph (Third Image)**
- **Purpose:** This graph overlays the maximum temperature data for all three locations, allowing for direct comparison.

**Interpretation:**

- **London** consistently has the highest peaks, while Swansea and Preston follow closely with slightly lower maximum temperatures. Seasonal trends, such as warmer summers and cooler winters, are clear across all locations.

Key Observations: London stands out as the warmest location, particularly in the summer months, while Preston remains cooler throughout the period.

## Challenges and Future work:

### Precipitation Data (2016-2024)
In the precipitation graph, data is visualised for three locations: London, Swansea, and Preston. However, it is important to note that the precipitation data for all London, Preston, and Swansea is missing for the years 2016 to 2021. As a result, the graph shows flat lines for these 3 locations, which reflect the absence of available data rather than actual precipitation levels.

One of the challenges we faced as a team was the missing precipitation data for London, Swansea and, Preston from 2016 to 2021. Although data cleaning was not my task, I worked closely with those responsible to understand the limitations and adapt our visualisations accordingly.

### My Role
In this group project, my primary responsibilities included:

- **Data Visualisation**: I was responsible for developing the data visualisation components using Matplotlib. This involved creating clear, informative graphs that highlighted the key trends in the dataset, such as average temperature, maximum temperature, and precipitation levels across London, Swansea, and Preston from 2016 to 2024.
  
- **Data Explanation**: I was tasked with explaining these trends to our project supervisor. This included preparing detailed summaries of our findings, discussing the implications of the identified trends, and addressing any limitations in the data, such as the missing precipitation records. My goal was to ensure that our supervisor had a clear understanding of the data's story and the insights it provided.

### My Learning Outcomes
- **Team Collaboration**: This project emphasised the importance of clear communication and coordination within a team, especially when dealing with large datasets and complex analyses.
- **Data Visualisation**: This project enhanced my skills in data visualisation, and further developed my ability to communicate complex data trends effectively to non-technical stakeholders despite the challenges posed by incomplete data.

### Future Work
As a group, we plan to:
- **Seek Additional Data**: Look for the missing precipitation data to complete our analysis.
- **Refine Visualisations**: Improve the way we handle and display incomplete data, possibly by using different markers or annotations.

### Acknowledgements
I would like to acknowledge the efforts of my team members who handled data cleaning and other crucial aspects of this project. Their work was integral to the success of our analysis.

