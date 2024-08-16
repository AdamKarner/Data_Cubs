Project 1

# Repository contains a Jupyter Notebook file titled crashesPy.ipynb.
# Output plot images will be found in folder Output Images.
# All resource files are contained inside the Resources folder with the exception of DivvyTripData.csv. This file is too large for our GitHub repo. Please download the file from the Google Drive link and place it in the resources folder.

# DivvyTripData.csv  -  https://drive.google.com/file/d/1ZQRhqmwzpJ6HCt-SO8WSwcUUTl55xjIZ/view?usp=drive_link

Divvy Usage in Chicago:
Does an increase in Divvy usage result in more accidents involving bicycles in the City of Chicago? This project will compare Divvy bike usage data from Divvy (https://divvybikes.com/system-data) and traffic crash data provided by the City of Chicago (https://data.cityofchicago.org/Transportation/Traffic-Crashes-People/u6pd-qa9d/about_data) to determine the effect the rise of Divvy has had on the number of bicycle-involved traffic accidents in Chicago since Q1 of 2020.

**Running `crashesPy.ipynb`:**
The script will search for a folder called "Output Images," and if it does not exist, it will create it. The script will then read in `.csv` data from the `.csv` files contained inside the "Resources" folder.

**Data Cleaning - Crash Data:**
The crash data obtained from the City of Chicago data portal will be filtered to include only records within the time frame of the Divvy Trip Data, starting from January 2020. The crash data contains duplicate records for each person involved in an incident, resulting in multiple rows for each individual incident. The script will search for all crash records involving bicycles and drop records with `CRASH_RECORD_ID`s that do not include bicycles. It will then check the remaining records for duplicate `CRASH_RECORD_ID`s to ensure that only one incident is recorded for any bicycle vs. bicycle incidents. After identifying the unique incidents involving bicycles, the `CRASH_DATE` for each record will be converted into the quarter of the year of the incident.

**Data Cleaning - Divvy Trip Data:**
The Divvy data needs minor formatting. The `started_at` value will be used to determine when the trip occurred, and it will be converted to date/time format and then grouped by quarter.

After cleaning the data, we observe that there were 7,886 reported accidents involving bicycles and roughly 23.25 million Divvy trips taken during the reviewed time period. The script will then create a series of subplots to compare the crash data and Divvy trip data to check for any relationships. These plots will be saved in the "Output Images" folder for review.

The first plot created, `Rides_Crashes_per_Quarter.png`, shows the number of Divvy rides taken each quarter and the number of bicycle-involved crashes reported to the city each quarter. Our goal here is to confirm or disprove the idea that more Divvy trips will result in more bicycle-related accidents. A visual review of the plots shows that the number of Divvy rides and the number of bicycle-related crashes both reach their highest and lowest values for the year during the same quarters. Both datasets peak during Q3 of each year, leading to the assumption that more bicycles on the road will result in more bicycle-related crashes. However, a closer review reveals that an increase or decrease in Divvy bicycles specifically does not necessarily cause the increase or decrease in the number of crashes that occur. Q3 of 2021 shows roughly 750,000 more Divvy trips compared to Q3 of 2020. Comparatively, crashes reported in Q3 of 2021 decreased slightly from Q3 of 2020. The following years show a steady decline in the number of Divvy trips taken, while also showing a steady increase in reported crashes. With the commonality in peaks and valleys being the time of year, and the peaks occurring during Q3, it can be assumed that both Divvy trips and crashes are heavily impacted by weather, indicating that the presence of more bicycles in general results in more accidents.

Taking the analysis from the first plots, we can now assume that the Divvy data is a good representation of bicycle usage in the city as a whole, and we can use that to further expand our review. The next plots generated, `Usage_Accidents_by_Hour_of_Day.png`, compare bicycle usage and crash data by the time of day they occurred. We see near-identical plots, with both sets of data peaking around the same times in the morning and afternoon. This again confirms that more bicycles result in more bicycle-related accidents, as well as showing that more accidents tend to occur during peak commuting times.

With that in mind, our next set of plots, `Usage_Accidents_by_Day_of_Week.png`, compares bicycle trips and accidents by the day of the week. We see that the trend continues, with one outlier that cannot be explained with our current data. Bicycle usage shows its largest jump, a 15.38% increase, from Friday to Saturday, indicating that tourism and leisure increase bicycle usage far more than work commuting. The plotting of the crash data by day of the week reveals an outlier and the first instance where higher bicycle usage and accident reporting do not rise and fall together. Friday results in a much higher rate of accidents than one would expect, showing a 16.67% increase from Thursday, while bicycle usage only increased by roughly 7% between those two days. Without further data, we are left to assume the reason for such an increase in accidents on Fridays when bicycle usage itself does not increase. This assumption may be confirmed with a later project. My hypothesis is that drinking and operating both vehicles and bicycles increases on Friday nights in the city, resulting in the higher reporting of accidents.

A bonus assumption that was explored for future review potential was the impact of increasing bicycle lanes on bicycle accidents in the city. Additional data was obtained from the City of Chicago Data Portal tracking the number of miles of bike lanes added each year. The immediate plot, `Bike_Lane_Additions_Crashes_per_Year.png`, seems to contradict this assumption, and further in-depth review would be needed.

**Conclusion:**
In conclusion, we can determine that the number of bicycles on the road directly correlates with the number of bicycle-related accidents that occur. While the data does not indicate that Divvy users themselves are primarily to blame, they contribute to the overall increase in bicycle usage, thereby indirectly resulting in more bicycle-related crashes in the areas where they operate.


