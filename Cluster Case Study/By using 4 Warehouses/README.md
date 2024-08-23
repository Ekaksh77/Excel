# Overview

A firm has many stores worldwide, with a significant number of stores in the USA. They aim to open warehouses to provide fast supply to consumers. The available data includes columns for Total Demands, Destination Latitude, Destination Longitude of Stores, and Cluster Number of the Firm.

## Project Objective

The goal is to determine the number and locations of warehouses to open, ensuring flexibility and the fastest routes to consumers.

## Summary

1. **Creating Additional Columns:**
   - Two new columns, `Lat*Demand` and `Long*Demand`, were created by multiplying Destination Latitude with Total Demand and Destination Longitude with Total Demand, respectively.

2. **Pivot Table Calculations:**
   - Generate a pivot table with the following columns: `Cluster Number`, `Sum of Lat*Demand`, `Sum of Long*Demand`, `Count of ClusterNo`, and `Sum of Total_Demand`.
   - Create two more columns:
     - `WH_Lat = Sum of Lat*Demand / Sum of Total_Demand`
     - `WH_Long = Sum of Long*Demand / Sum of Total_Demand`

3. **Distance Calculation:**
   - Calculate the distance of all predicted warehouses from each destination warehouse. Create the following columns: `Distance from WH_0`, `Distance from WH_2`, `Distance from WH_3`, and `Distance from WH_4`.
   - Use the formula below to calculate distances:
     ```text
     2 * 6371 * ASIN(SQRT((SIN((LAT2*(3.14159/180)) - LAT1*(3.14159/180)) / 2)^2 + COS(LAT2*(3.14159/180)) * COS(LAT1*(3.14159/180)) * SIN((LONG2*(3.14159/180) - LONG1*(3.14159/180)) / 2)^2))
     ```
   - Identify the minimum distance and determine the corresponding warehouse number.

4. **Pivot Table for Warehouse Data:**
   - Use a pivot table to generate the following columns: `Warehouse Number`, `Average of Min_Distance`, `Count of Final Nearest WH`, `Min of Min_Distance`, `Max of Min_Distance`, and `Sum of Total_Demand`.

5. **Demand Analysis:**
   - Create two additional columns: `Demand%` and `Sum of Demand`. Calculate the contribution of each demand as `Total Demand / Sum of Demands`.

6. **Visualization in Tableau:**
   - Upload all the details into Tableau and create the relevant charts.

## Key Observation

Warehouse number 4 contributes 33% alone. In comparison, Warehouse number 0 contributes 23%, Warehouse number 2 contributes 24%, and Warehouse number 3 contributes 19%. This distribution suggests that the current number of warehouses is optimal to balance the workload effectively.
