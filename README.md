FLIGHT DELAY ANALYSIS
 Flight Delay & On-Time Performance Analysis | Power BI | excel
 Project Overview

This project focuses on analysing airline flight delays and on-time performance using Microsoft Power BI and Excel. The dashboard provides insights into flight operations, departure and arrival delays, airline performance, aircraft utilisation and route-wise flight distribution.

The main objective is to identify patterns in flight delays, evaluate airline operational performance and understand the factors associated with delayed flights through interactive visualisations.

Project Objectives

- Analyse overall flight operations and performance.
- Evaluate on-time departure and arrival performance.
- Compare operational performance across different airlines.
- Identify routes with higher flight volumes.
- Analyse flight distribution by aircraft type.
- Investigate delay patterns across different departure time periods.
- Identify major reasons contributing to flight delays.
- Explore the relationship between flight distance and delay duration.

Tools & Technologies

- Microsoft Power BI
- Power Query – Data Cleaning and Transformation
- DAX – Calculated Columns and Measures
- Data Visualization and Exploratory Data Analysis

Data Cleaning & Transformation

Data preparation was performed using Power Query in Excel and calculated columns in Power BI.

Key activities included:

- Examining the dataset for inconsistencies.
- Reviewing missing and invalid values.
- Transforming data types where required.
- Creating calculated columns for flight status and departure time categories.
- Preparing visuals for delay analysis and performance calculations.

cards

The dashboard includes the following performance indicators:

- Total Flights
- Total Routes
- Total Airlines
- Total Flight Distance
- On-Time Arrival Flights
- On-Time Arrival Performance (%)
- Maximum Delay
- Average of Arrival Delay
- Average of Departure Delay

Dashboard Visualizations

1. Flight Overview

- Total Flights by Airline and Aircraft Type(Clustered Column Chart)
- Flight Distribution by Route(Bar Chart)
- Flight Distribution by Origin and Destination(map)
- Flight Status Distribution(Pie Chart)

2. Flight Delay Analysis

- On-Time Departure vs Arrival Performance by Airline
- On-Time Performance by Aircraft Type
- Flight Performance by Departure Time Category
- Delay Reason Analysis
- Departure and Arrival Flight Status Comparison
- Route-wise Flight Analysis
- Flight Distribution by Departure Time Period
- Decomposition Tree for flight distribution by origin, destination and departure time category.
- Scatter Plot to investigate the relationship between flight distance and delay duration.
- Matrix Analysis to compare airline performance across departure time categories.

Slicers

- Airline
- Aircraft Type
- Origin
- Destination
- Delay Reason
- Arrival Flight Status

DAX Calculations

1. DAX Measures

1 Total Flights
Total Flights =COUNTROWS('flight_delays1')

2 Total Routes
Total Routes =DISTINCTCOUNT('flight_delays1'[ROUTE])

3 Total Airlines
Total Airlines =DISTINCTCOUNT('flight_delays1'[Airline])

4 Total Flight Distance
Total Flight Distance =SUM('flight_delays1'[Distance])

5 On-Time Arrival Flights
On-time Arrival Flights =CALCULATE([Total Flights], 'flight_delays1'[ArrivalDelay] <= 0)

6 On-Time Arrival Performance %
On-time Arrival Performance % =DIVIDE([On-time Arrival Flights],[Total Flights],0)

7 On-Time Departure Flights
On-time Departure Flights =CALCULATE([Total Flights],'flight_delays1'[Departure Delay] <= 0)

8 On-Time Departure Performance %
On-time Departure Performance % =DIVIDE([On-time Departure Flights],[Total Flights],0)

9 Maximum Delay
Maximum Delay =MAX('flight_delays1'[ArrivalDelay])

2. Calculated Columns

1 Departure Flight Status
Departure Flight Status = SWITCH(TRUE(),flight_delays1[Departure Delay]< 0, "Early",flight_delays1[Departure Delay] = 0, "On Time",flight_delays1[Departure Delay] > 0, "Delayed")

2 Arrival Flight Status
Arrival Flight Status = SWITCH(TRUE(),flight_delays1[ArrivalDelay] < 0, "Early",flight_delays1[ArrivalDelay] = 0, "On Time",flight_delays1[ArrivalDelay] > 0, "Delayed")

3 Departure Time Category

Departure Time Category = VAR HourValue =HOUR(flight_delays1[ScheduledDeparture])RETURN SWITCH(TRUE(),HourValue < 6, "Night",HourValue < 12, "Morning",HourValue < 18, "Afternoon","Evening")

4 Delay Reason Corrected
A cleaned delay-reason field was used 

Conclusion

This project demonstrates how Power BI can be used to transform raw flight data into meaningful business insights.
Through interactive dashboards, KPI tracking, DAX calculations and advanced visualisations, the analysis provides a comprehensive view of airline operations and flight performance.

