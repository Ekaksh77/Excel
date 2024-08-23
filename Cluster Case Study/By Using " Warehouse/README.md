# Overview

A firm has many stores worldwide, with a large volume of stores in the USA. They would like to open warehouses to provide fast supply to consumers. We have columns for Total Demands, Destination Latitude, Destination Longitude of Stores, and Cluster Number of the Firm.

## Project Objective

We need to determine the number and locations of warehouses to open, making the supply chain more flexible and ensuring the fastest route to consumers.

## Summary

1. **Create Additional Columns:**
   - We first created two additional columns `Lat*Demand` and `Long*Demand` by multiplying Destination Latitude with Total Demand, and Destination Longitude with Total Demand, respectively.

2. **Pivot Table Calculations:**
   - Use a pivot table to generate the following columns: `Cluster Number`, `Sum of Lat*Demand`, `Sum of Long*Demand`, `Count of ClusterNo`, and `Sum of Total_Demand`.
   - Create two additional columns `WH_Lat` and `WH_Long` using the formulas:
     - `WH_Lat = Sum of Lat*Demand / Sum of Total_Demand`
     - `WH_Long = Sum of Long*Demand / Sum of Total_Demand`

3. **Calculate Distances:**
   - Calculate the distance of all predicted warehouses from each destination warehouse. Create three additional columns: `Distance from WH_0`, `Distance from WH_1`, and `Distance from WH_2`.
   - Use the following formula to calculate distances:
     ```text
     2 * 6371 * ASIN(SQRT((SIN((LAT2*(3.14159/180)) - LAT1*(3.14159/180)) / 2)^2 + COS(LAT2*(3.14159/180)) * COS(LAT1*(3.14159/180)) * SIN((LONG2*(3.14159/180) - LONG1*(3.14159/180)) / 2)^2))
     ```
   - Identify the minimum distance and determine the nearest warehouse number.

4. **Pivot Table for Warehouse Data:**
   - Use a pivot table to generate the following columns: `Warehouse Number`, `Average of Min_Distance`, `Count of Final Nearest WH`, `Min of Min_Distance`, `Max of Min_Distance`, and `Sum of Total_Demand`.

5. **Demand Analysis:**
   - Create two additional columns: `Demand%` and `Sum of Demand`. Calculate the contribution of each demand as `Total Demand / Sum of Demands`.

6. **Visualization in Tableau:**
   - Upload all the details into Tableau and create the relevant charts.

## Key Observation

There is a 79% contribution by Warehouse number 2, while Warehouse number 0 contributes 21%. We need to open two more warehouses to support Warehouse number 2, reducing its workload from 79% to at least 25% each. Otherwise, the work could become more chaotic and messy.
