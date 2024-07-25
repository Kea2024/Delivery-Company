# Delivery Company

### Project Overview
The goal is to  make a report for an Indian delivery company about delivery time to compare the company’s performance with competitors.

![Screenshot 2024-05-09 011537](https://github.com/user-attachments/assets/24d79857-1e10-4b72-8aab-6262e7db823e)


## Table of Contents
- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Cleaning/Preparation](#data-cleaningpreparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results/Findings](#resultsfindings)
- [Recommendations](#recommendations)
- [Limitations](#limitations)

### Data Sources
 The datasets used for this analysis are:
 - delivery_statistics.csv

### Tools
- Power BI - cleaning, data analysis and data visualization

### Data Cleaning/Preparation

In the initial data preparation phase, we performed the following tasks:
1. Data loading and inspection
2. Handling missing values
3. Data cleaning and formatting

### Exploratory Data Analysis

EDA involved the sales data to answer key questions, such as:

- What do you suggest the delivery company do so it can collect better data and get more precise results?

### Data Analysis

``` Power BI
= Table.AddColumn(#"Changed Type", "Text Range", each Text.Middle([Weatherconditions], 11, 21), type text)

= Table.RenameColumns(#"Inserted Text Range",{{"Text Range", "Weather Conditions"}}),

= Table.RemoveColumns(#"Renamed Columns",{"Weatherconditions"}),

= Table.ReplaceValue(#"Removed Columns","NaN","No Data",Replacer.ReplaceText,{"Weather Conditions"}),

= Table.ReplaceValue(#"Replaced Value","NaN","No Data",Replacer.ReplaceText,{"Road_traffic_density"}),

= Table.SelectRows(#"Replaced Value1", each [Time_Orderd] <> null and [Time_Orderd] <> ""),

= Table.SelectRows(#"Filtered Rows", each [Delivery_person_Ratings] <> null and [Delivery_person_Ratings] <> ""),

= Table.RenameColumns(#"Filtered Rows1",{{"Time_taken(min)", "Delivery Time"}}),

= Table.SelectRows(#"Renamed Columns1", each [Delivery_location_latitude] <> null and [Delivery_location_latitude] <> ""),

= Table.SelectRows(#"Filtered Rows2", each [Restaurant_latitude] > 0),

= Table.SelectRows(#"Filtered Rows3", each [Restaurant_longitude] > 0),

= Table.SelectRows(#"Filtered Rows4", each true),

= Table.SelectRows(#"Filtered Rows5", each [Delivery_location_latitude] <> null and [Delivery_location_latitude] <> ""),

= Table.SelectRows(#"Filtered Rows6", each ([Delivery_location_longitude] <> null and [Delivery_location_longitude] <> 88.364127 and [Delivery_location_longitude] <> 88.37068 and [Delivery_location_longitude] <> 88.37231 and [Delivery_location_longitude] <> 88.374878 and [Delivery_location_longitude] <> 88.38231 and [Delivery_location_longitude] <> 88.382885 and [Delivery_location_longitude] <> 88.384127 and [Delivery_location_longitude] <> 88.385507 and [Delivery_location_longitude] <> 88.414453 and [Delivery_location_longitude] <> 88.422885 and [Delivery_location_longitude] <> 88.424453 and [Delivery_location_longitude] <> 88.424878 and [Delivery_location_longitude] <> 88.442504 and [Delivery_location_longitude] <> 88.442885 and [Delivery_location_longitude] <> 88.454453 and [Delivery_location_longitude] <> 88.463452 and [Delivery_location_longitude] <> 88.480581 and [Delivery_location_longitude] <> 88.483452 and [Delivery_location_longitude] <> 88.493187 and [Delivery_location_longitude] <> 88.503187 and [Delivery_location_longitude] <> 88.523452 and [Delivery_location_longitude] <> "") and ([City] <> "NaN ")),

= Table.SelectRows(#"Filtered Rows7", each [Delivery_location_longitude] < 80),

= Table.AddColumn(#"Filtered Rows8", "Delivery_time", each [Delivery Time]),

= Table.AddColumn(#"Added Custom", "Last Characters", each Text.End([Delivery_time], 2), type text),

= Table.TransformColumnTypes(#"Inserted Last Characters",{{"Last Characters", Int64.Type}, {"Time_Orderd", type time}}),

= Table.RemoveColumns(#"Changed Type1",{"Delivery_time", "Last Characters"}),
```
### Results/Findings:

The analysis results are summarized as follows:
1. At 30, Fog had the highest Average of DT and was 27.29% higher than Sunny, which had the lowest Average of DT at 24.
2. ﻿Across all 7 Weather Conditions, Average of DT ranged from 24 to 30.
3. Metropolitian accounted for 78.10% of Sum of Delivery_location_longitude.
4. Motorcycle has the highest average of DT despite any weather conditions.

### Recommendations:
- Provide customers with options for delivery such as contactless drop-offs at a designated location to minimize exposure to weather conditions.
- Keep customers informed if there are delays due to weather conditions. They'll appreciate the transparency and understanding.

### Limitations:

There were a lot of outliers when it comes to the geographical location that can affect the accuracy of my conclusion.






