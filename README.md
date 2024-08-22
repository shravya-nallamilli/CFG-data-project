# Weather Data Analysis☁️

A group project undertaken as part of the Code First Girls to retrieve, clean, and analyse historical weather data for specific locations in the UK.

## Key features

Data Retrieval: Fetches historical monthly weather data from the Meteostat API.

Data Cleaning: Processes and cleans the data to handle missing values and irrelevant columns.

Data Analysis & Visualisation: Analyses temperature, precipitation trends, and provides tools to visualise weather trends and patterns over time.

## Installation

1. **Install the necessary dependencies**:

 Necessary libraries such as `pandas`, `numpy`, and `matplotlib` are imported, and the `meteostat` package is used to fetch historical weather data.
   
   ```python
   !pip install meteostat
   import pandas as pd
   import numpy as np
   import matplotlib.pyplot as plt
   from datetime import datetime
   from meteostat import Point, Monthly
   ```
2. **Data retrieval - Define the Time Period**:
The time period is defined to capture weather data three years before, during, and after the COVID-19 pandemic.

```Python
start = datetime(2016, 6, 7)
end = datetime(2024, 6, 7)
```

3.  **Location Points Creation**:
Points for London, Swansea, and Preston are created using latitude and longitude coordinates, which are essential for fetching region-specific weather data.

```Python
london = Point(51.5072, -0.1276, 50)
swansea = Point(51.6208, -3.9432)
preston = Point(53.7628, -2.7045)
```

# Fetch monthly weather data
Fetch monthly weather data for each location using the `meteostat` library. The data is stored in separate dataframes for London, Swansea, and Preston.

```Python
london_monthly_data = Monthly(london, start, end).fetch()
swansea_monthly_data = Monthly(swansea, start, end).fetch()
preston_monthly_data = Monthly(preston, start, end).fetch()
```
5. **Regional Data Consolidation**:
Store the dataframes for each city into a list called regional_data, which will be used for further analysis and visualisations in the project.

```python
regional_data = [london_monthly_data, swansea_monthly_data, preston_monthly_data]
```

## Data Cleaning

To ensure the data is ready for analysis, the following steps were taken to clean and preprocess the data:

1. **Initial Data Inspection**:  
   Each dataset (London, Swansea, Preston) was inspected to understand its structure and identify any missing values.
   
   ```python
   for details in regional_data:
       details.info()
   ```
2. **Column Renaming**:  
The columns were renamed to more descriptive names to improve readability. For example, tavg was renamed to average_temp, tmin to minimum_temp, and tmax to maximum_temp.

```python
regions.rename(columns={'time':'date','tavg':'average_temp','tmin': 'minimum_temp', 'tmax':'maximum_temp'}, inplace=True)
```
3. **Dropping unnecessary Columns**:  
Columns that were not required for the analysis (wspd, pres, minimum_temp, tsun) were removed from the datasets.

```python
regions.drop(columns=['wspd','pres','minimum_temp','tsun'], inplace=True)
```

4.  **Handling Missing Data**:
Missing values in the maximum_temp, average_temp, and prcp columns were filled with the mean value of the respective columns. This ensures that the analysis is not skewed by NaNs.

```python
regions["maximum_temp"] = regions["maximum_temp"].replace({np.nan: regions["maximum_temp"].mean()})
regions["average_temp"] = regions["average_temp"].replace({np.nan: regions["average_temp"].mean()})
regions["prcp"] = regions["prcp"].replace({np.nan: regions["prcp"].mean()})
```

5. **Final Data Review**:
After cleaning, the datasets were reviewed to ensure that all changes were correctly applied

```Python
print(regions.round(1))
```
## Data Analysis and Visualisation

In this step, we analyse the weather data by comparing the average and maximum temperatures across the three locations: London, Swansea, and Preston. The data is visualised using matplotlib with multiple subplots to clearly illustrate the differences and trends over time.

1. **Average Temperature Visualisation:**

To begin, we create a figure with three vertically arranged subplots, each representing the average temperature for London, Swansea, and Preston. This allows for a direct comparison across the three locations.

```python
# Create subplots for average temperature
fig, axes = plt.subplots(3, 1, figsize=(10, 12), sharex=True)

# Plot data for London, Swansea, and Preston
axes[0].plot(london_monthly_data.index, london_monthly_data['average_temp'], label='London', color='green')
axes[1].plot(swansea_monthly_data.index, swansea_monthly_data['average_temp'], label='Swansea', color='red')
axes[2].plot(preston_monthly_data.index, preston_monthly_data['average_temp'], label='Preston', color='blue')

# Titles and labels
fig.suptitle('UK Average Temperature Comparison (2016-2024)')
plt.xlabel('Date')
fig.text(0.04, 0.5, 'Temperature (°C)', va='center', rotation='vertical')
plt.tight_layout()

```
2. **Maximum Temperatures Visualisation**

Similarly, another figure with three subplots is created to illustrate the maximum temperatures for each location. This helps in understanding the extreme weather conditions in each region.

```Python
# Create subplots for maximum temperature
fig, axes = plt.subplots(3, 1, figsize=(10, 12), sharex=True)

# Plot data for London, Swansea, and Preston
axes[0].plot(london_monthly_data.index, london_monthly_data['maximum_temp'], label='London', color='green')
axes[1].plot(swansea_monthly_data.index, swansea_monthly_data['maximum_temp'], label='Swansea', color='red')
axes[2].plot(preston_monthly_data.index, preston_monthly_data['maximum_temp'], label='Preston', color='blue')

# Titles and labels
fig.suptitle('UK Maximum Temperature Comparison (2016-2024)')
plt.xlabel('Date')
fig.text(0.04, 0.5, 'Temperature (°C)', va='center', rotation='vertical')
plt.tight_layout()
```

3.  **Combined Maximum Temperature Plot**

Finally, we plot the maximum temperatures of all three locations on a single graph for a direct comparison.

```Python
plt.figure(figsize=(10, 6))
plt.plot(london_monthly_data.index, london_monthly_data['maximum_temp'], label='London', color='lightblue')
plt.plot(swansea_monthly_data.index, swansea_monthly_data['maximum_temp'], label='Swansea', color='orange')
plt.plot(preston_monthly_data.index, preston_monthly_data['maximum_temp'], label='Preston', color='red')

plt.title('Maximum Temperature Comparison (2016-2024)')
plt.xlabel('Date')
plt.ylabel('Temperature (°C)')
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()
```

4. **Preciptation data**
   
This section demonstrates how to visualise precipitation data for London, Swansea, and Preston from 2016 to 2024.

```python
# Create a figure for the plot
plt.figure(figsize=(10, 6))

# Plot precipitation data for each location
plt.plot(london_monthly_data.index, london_monthly_data['prcp'], label='London', linestyle='-', marker='*', color='lightblue', lw=3, ms=10)
plt.plot(swansea_monthly_data.index, swansea_monthly_data['prcp'], label='Swansea', linestyle='-', marker='D', color='orange')
plt.plot(preston_monthly_data.index, preston_monthly_data['prcp'], label='Preston', linestyle='-', marker='H', color='red', lw=1)

# Add titles, labels, and legend
plt.title('UK Precipitation Data: Three Geographical Locations 2016-2024')
plt.xlabel('Date')
plt.ylabel('Precipitation (mm)')
plt.legend()
plt.grid(True)
plt.tight_layout()

# Display the plot
plt.show()
```

**Summary**

Purpose: The code plots precipitation data for London, Swansea, and Preston.

Customisation: The plot uses different colors and markers to differentiate between the locations.

Features: Includes a title, axis labels, legend, and grid for clarity.
