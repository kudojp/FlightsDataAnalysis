# Flights Data Analysis
## by Daiki Kudo


## Project detail
このプロジェクトでは2008年の米国の飛行機の飛行データをもとに、飛行機の到着の遅延が"NASDelay", "LateAircraftDelay", "CarrierDelay", "WeatherDelay","SecurityDelay". "NSADelay"の要素のどれに大きく影響させるかを分析しています。

飛行機の遅延時間は地上での遅れ(Departure Delay)と空での遅れ(Elapsed Time Delay)の合計として表されます。結論としては、Departure delayが長いほどCarrier DelayとWeather Delayの影響を大きく受けていて、一方でElapsed Time Delayが長いほどNSADelayの影響を大きく受けていることを発見しました。
(本プロジェクトに関しては機械学習モデルの作成まではしておりません)

├── flightsdata_explanation.ipynb
├── flightsdata_explanation.slides.html
├── flightsdata_exploration.html
├── flightsdata_exploration.ipynb
├── output_toggle.tpl
└── readme.md

flightsdata_expl"O"ration.htmlではデータの把握（一変数の分布、二変数の関係、三変数の関係）含め全ての過程を試行錯誤含め最初から最後まで残してあります。

flightsdata_expl"A"nation.htmlではexplorationの内容を要約したものです。会議のプレゼンテーションなどで説明する際にはこちらを使います。

## Dataset

The data consists of approximately 7 million domestic records in United States. This records include date, distance, arrival time and other various features such as delay factors. The dataset (2008.csv) can be downloaded from Statistical Computing
Statistical Graphics [here](http://stat-computing.org/dataexpo/2009/the-data.html),  
with feature details available, [here](https://www.transtats.bts.gov/Fields.asp?Table_ID=236).

## Summary of Findings

* Arrival delay can be broken down into Departure Delay and Elapsed Time Delay. Elaped Time Delay is the lag between Actual Elapsed Time and CRS(scheduled) Elapsed Time. This means how many minutes passengers had to spend their extra time in the airplanes. I decided to investigate these 2 delays separately. I found that Departure Delay is generally far longer than Elapsed Time.　Though Departure Delay was right skewed and takes rather higher values, the Elapsed Time Delay is symmetric and takes rather lower values. Out of expectation, These 2 delays did not show clear correlationship with distance.

* There are 5 delay factors which are in the dataset. They are "NASDelay", "LateAircraftDelay", "CarrierDelay", "WeatherDelay" and "SecurityDelay". "NSADelay" happened most frequently followed by "LateAircraftDelay" and "CarrierDelay". "Security Delay" was found to have very little effect compared with other 4 factors, so I investigated only these 4 factors. These 4 factors did not show clear correlationship with distance.

```
* Carrier Delay
Carrier delay is within the control of the air carrier. Examples of occurrences that may determine carrier delay are: aircraft cleaning, aircraft damage, awaiting the arrival of connecting passengers or crew, baggage, bird strike, cargo loading, catering, computer, outage-carrier equipment, crew legality (pilot or attendant rest), damage by hazardous goods, engineering inspection, fueling, handling disabled passengers, late crew, lavatory servicing, maintenance, oversales, potable water servicing, removal of unruly passenger, slow boarding or seating, stowing carry-on baggage, weight and balance delays.
* Late Arrival Delay
Arrival delay at an airport due to the late arrival of the same aircraft at a previous airport. The ripple effect of an earlier delay at downstream airports is referred to as delay propagation.
* NAS Delay
Delay that is within the control of the National Airspace System (NAS) may include: non-extreme weather conditions, airport operations, heavy traffic volume, air traffic control, etc. Delays that occur after Actual Gate Out are usually attributed to the NAS and are also reported through OPSNET.
* Security Delay
Security delay is caused by evacuation of a terminal or concourse, re-boarding of aircraft because of security breach, inoperative screening equipment and/or long lines in excess of 29 minutes at screening areas.
Weather Delay
Weather delay is caused by extreme or hazardous weather conditions that are forecasted or manifest themselves on point of departure, enroute, or on point of arrival.
```

* Finally, I visualized how the length of 4 delay factors were distributed by clustering the Departure Delay time length into 4 levels. Distance did not have a big effect on the delay time, so I did not include it in this visualization. The Departure Delay was divided into 5 levels and the distribution of each of 4 factors n each level,  were shown by clustered violin plot. It showed that the longer Departure Delay time is, the more it was associated with with longer CarrierDelay and WeatherDelay. Then I focused on Elapsed Time Delay and reproduced the plot with 2 levels of ElapsedTimeDelay instead of DepartureDelay. It suggested that only NAS Delay factor was associated with longer DepartureDelay.

* In the process of exploration, I found that the data of flights which connected continental airport and Hawaiian airport tended to have more outliers, so I decided to exclude such flights history in this research. Last but not least, I removed records which were cancelled or diverted flights because they are not my main interests.


## Key Insights for Presentation

* For the presentation, I focus on the relationship between the distribution of each 4 factors according to the length of DepartureDelay / ElapsedTimeDelay.

* I start by comparing these 2 delays in the scatterplot, followed by the attributes of 4 delay factors by the barchart of each occurrence rate and by the violinplot of these 4 factors' delay time.  Afterwards, I show that distance is not a big factor of delay time. Then, I will reveal the main 2 findings of this analysis. I use the clustered violinplot which is clusterded by DepartureDelay levels. Another plot which is clustered by ElapsedTimeDelay would follow it for comparison.
