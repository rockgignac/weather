# Does It Rain More in Seattle Than in Miami?

This project uses daily weather data from NOAA to answer the question of whether it rains more in Seattle, WA than in Miami, FL. The question is looked at in two ways: the amount of precipitation in each city and how often it rains (the proportion of days with any precipitation).

## Data

The data are daily weather summaries from the National Oceanic and Atmospheric Administration (NOAA), downloaded from Climate Data Online: https://www.ncei.noaa.gov/cdo-web/

- Seattle: Seattle-Tacoma International Airport (station ID USW00024233)
- Miami: Miami International Airport (station ID USW00012839)
- Date range: January 1, 2018 to December 31, 2022

The raw data file is `data/4406076.csv`.

## Data Analysis

### Steps

1. Loaded the raw NOAA data and inspected the size, column types, stations, and date range.
2. Split the data into separate Seattle and Miami data frames and converted the date column from text to a datetime type.
3. Checked for duplicate dates and dates outside the 2018–2022 range (none were found).
4. Identified 3 missing precipitation values in Seattle (December 2021).
5. Joined the Seattle and Miami data on date, keeping only the date and precipitation columns.
6. Reshaped the data into a tidy (long) format and renamed the columns to be lowercase and understandable (`date`, `city`, `precipitation`).
7. Filled in the 3 missing values using Seattle's average precipitation for the same day of the year.
8. Created derived variables: `day_of_year`, `month`, and `any_precipitation` (whether there was any precipitation that day).
9. Explored the data with summary statistics, line plots, bar graphs, and box plots, comparing the cities overall and by month.
10. Used independent samples t-tests to compare mean precipitation between the cities in each month, and proportions z-tests to compare the proportion of days with precipitation in each month.

### Files

- Analysis notebook: `Weather_Data.ipynb`
- Clean data file: `data/clean_seattle_miami_precipitation.csv`

The clean data file contains the columns `date`, `city`, `precipitation`, and `day_of_year`.

### Results

Overall, it does not rain more in Seattle than in Miami. Miami averages more precipitation per day (0.19 inches vs. 0.11 inches), and the two cities have precipitation on about the same proportion of days (about 42% in Seattle and 41% in Miami). The answer depends on the season. Seattle gets significantly more rain and has rain more often in the winter, while Miami gets significantly more rain and has rain more often in the summer.

## Requirements

The notebook uses Python with pandas, numpy, matplotlib, seaborn, scipy, and statsmodels. All of these are included in Anaconda.
