# Overview

The firm operates stores worldwide, with a significant concentration in the USA. To enhance consumer satisfaction by ensuring faster supply, the firm plans to open new warehouses. We have data columns for total demand, destination latitude, destination longitude of stores, and cluster numbers.

**Project Objective:** Determine the optimal number and locations of warehouses to ensure flexibility and the fastest delivery routes to consumers.

# Summary

1. **Create Weighted Coordinates:**
   - Add two new columns: `Lat*Demand` and `Long*Demand`, by multiplying the destination latitude and longitude with the total demand.

2. **Calculate Weighted Averages Using Pivot Table:**
   - Use a pivot table with the following columns:
     - `Cluster Number`
     - `Sum of Lat*Demand`
     - `Sum of Long*Demand`
     - `Count of ClusterNo`
     - `Sum of Total_Demand`
   - Calculate warehouse coordinates using:
     - `WH_Lat = Sum of Lat*Demand / Sum of Total_Demand`
     - `WH_Long = Sum of Long*Demand / Sum of Total_Demand`

3. **Determine Warehouse Distances:**
   - Calculate the distance from each predicted warehouse to the destination stores using the formula:
     ```
     2 * 6371 * ASIN(SQRT((SIN((LAT2*(3.14159/180))-LAT1*(3.14159/180))/2)^2 +
     COS(LAT2*(3.14159/180)) * COS(LAT1*(3.14159/180)) * SIN(((LONG2*(3.14159/180)-LONG1*(3.14159/180))/2))^2))
     ```
   - Add columns for the distance from each warehouse (`WH_0`, `WH_2`, `WH_3`).
   - Identify the minimum distance and corresponding warehouse number.

4. **Summarize Data Using Pivot Table:**
   - Create a pivot table with the following columns:
     - `Warehouse Number`
     - `Average of Min_Distance`
     - `Count of Final Nearest WH`
     - `Min of Min_Distance`
     - `Max of Min_Distance`
     - `Sum of Total_Demand`

5. **Analyze Demand Contribution:**
   - Add columns for `Demand%` and `Sum of Demand` to analyze the contribution of each demand by dividing `Total Demand` by the `Sum of Demands`.

6. **Visualization:**
   - Upload the processed data into Tableau and create visual charts.

# Key Observations

- **Warehouse Number 2** handles 54% of the total demand, indicating a heavy workload.
- **Warehouse Number 0** accounts for 26% of the demand.
- **Warehouse Number 3** contributes 19% of the demand.
- To reduce the strain on Warehouse Number 2 and balance the workload to approximately 25% per warehouse, an additional warehouse may be needed. Without this, operations could become chaotic.
