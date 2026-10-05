# Does It Rain More in Seattle Than in Miami?

## Project Overview

Seattle has a reputation as one of the rainiest cities in the United States. This project tests that reputation by comparing daily precipitation in Seattle, WA and Miami, FL from 2018 to 2022 using NOAA weather station data. The question is answered in two ways: the amount of precipitation in each city and how often it rains (the proportion of days with any precipitation).

The key finding is that it does not rain more in Seattle than in Miami. Miami gets more precipitation on average, and the two cities have rain on about the same proportion of days. However, the answer depends on the season. Seattle gets more rain, and rain more often, in the winter, while Miami gets more in the summer.

## Data

The data are daily weather summaries from the National Oceanic and Atmospheric Administration (NOAA), downloaded from Climate Data Online: https://www.ncei.noaa.gov/cdo-web/

The data come from the Global Historical Climatology Network – Daily (GHCN-Daily) dataset: https://www.ncei.noaa.gov/products/land-based-station/global-historical-climatology-network-daily

- Seattle: Seattle-Tacoma International Airport (station ID USW00024233)
- Miami: Miami International Airport (station ID USW00012839)
- Date range: January 1, 2018 to December 31, 2022

Files in this repository:

- Raw data: `data/4406076.csv`
- Clean data: `data/clean_seattle_miami_precipitation.csv` (columns: `date`, `city`, `precipitation`, `day_of_year`)

## Analysis

All data cleaning and analysis are in the notebook `Weather_Data.ipynb`.

**Data cleaning** (notebook sections "Inspecting the Data" through "Saving the Clean Data"):

1. Loaded the raw NOAA data and inspected the size, column types, stations, and date range.
2. Split the data by station and converted the date column from text to a datetime type.
3. Checked for duplicate dates and dates outside the 2018–2022 range (none were found).
4. Identified 3 missing precipitation values in Seattle (December 2021).
5. Joined the Seattle and Miami data on date, reshaped it into a tidy (long) format, and renamed the columns.
6. Filled in the 3 missing values with Seattle's average precipitation for the same day of the year.
7. Saved the clean data to `data/clean_seattle_miami_precipitation.csv`.

**Analysis** (notebook sections "Exploring the Data" and "Statistical Tests"):

1. Compared the cities using summary statistics, line plots, bar graphs, and box plots, both overall and by month.
2. Created an `any_precipitation` variable to compare how often it rains in each city.
3. Used independent samples t-tests to compare mean daily precipitation between the cities in each month.
4. Used proportions z-tests to compare the proportion of days with precipitation between the cities in each month.

## Results

- **Amount:** Miami averages more precipitation per day than Seattle (0.19 inches vs. 0.11 inches). Seattle has a significantly higher mean in January, February, March, and December, while Miami has a significantly higher mean from May through September.
- **Frequency:** The two cities have precipitation on about the same proportion of days overall (42.6% in Seattle and 41.1% in Miami). Seattle has rain significantly more often from November through April, and Miami has rain significantly more often from May through September.

Seattle's rainy reputation likely comes from its winters, when it rains on about two out of every three days, even though Miami gets more rain over the full year.

The full write-up of the results is in `[communication document file name]`.

## Authors

Rock Gignac — [GitHub](https://github.com/rockgignac)

## License

This project is licensed under the MIT License. See the `LICENSE` file for details. The NOAA data are in the public domain.

## Acknowledgments

- NOAA National Centers for Environmental Information for providing the weather data.
- AI tools were used to help learn the Python syntax and methods for the statistical tests, as noted in the notebook.
