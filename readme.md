# Flights Data Analysis
## by Daiki Kudo


## Dataset

The data consists of approximately 7 million domestic records in United States. This records include date, distance, arrival time and other various features such as delay factors. The dataset (2008.csv) can be downloaded from Statistical Computing
Statistical Graphics [here](http://stat-computing.org/dataexpo/2009/the-data.html),  
with feature details available, [here](https://www.transtats.bts.gov/Fields.asp?Table_ID=236).

## Summary of Findings

* Arrival delay is the total of Departure Delay and Elapsed Time Delay, and I decided to investigate these 2 delays. I found that Departure Delay is generally far longer than Elapsed Time.　Though Departure Delay was left skewed and takes rather higher values, the Elapsed Time Delay is symmetric and takes rather lower values. Out of expectation, These 2 delays did not show clear correlationship with distance.

* There are 5 delay factors which are in the dataset. They are "NASDelay", "LateAircraftDelay", "CarrierDelay", "WeatherDelay" and "SecurityDelay". "NSADelay" happened most frequently followed by "LateAircraftDelay" and "CarrierDelay". "Security Delay" was found to have very little effect compared with other 4 factors, so I investigated only these 4 factors. These 4 factors did not show clear correlationship with distance.

* Finally, I visualized how the length of 4 delay factors were distributed by clustering the Departure Delay time length into 4 levels. Distance did not have a big effect on the delay time, so I did not include it in this visualization. The Departure Delay was divided into 5 levels and the distribution of each of 4 factors n each level,  were shown by clustered violin plot. It showed that the longer Departure Delay time is, the more it was associated with with longer CarrierDelay and WeatherDelay. Then I focused on Elapsed Time Delay and reproduced the plot with 2 levels of ElapsedTimeDelay instead of DepartureDelay. It suggested that only NAS Delay factor was associated with longer DepartureDelay.

* In the process of exploration, I found that the data of flights which connected continental airport and Hawaiian airport tended to have more outliers, so I decided to exclude such flights history in this research. Last but not least, I removed records which were cancelled or diverted flights because they are not my main interests.


## Key Insights for Presentation

* For the presentation, I focus on the relationship between the distribution of each 4 factors according to the length of DepartureDelay / ElapsedTimeDelay.

* I start by comparing these 2 delays in the scatterplot, followed by the attributes of 4 delay factors by the barchart of each occurrence rate and by the violinplot of these 4 factors' delay time.  Afterwards, I show that distance is not a big factor of delay time. Then, I will reveal the main 2 findings of this analysis. I use the clustered violinplot which is clusterded by DepartureDelay levels. Another plot which is clustered by ElapsedTimeDelay would follow it for comparison.
