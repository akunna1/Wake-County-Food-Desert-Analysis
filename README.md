# Food Desert Analysis in Wake County 🗺️

## Project Overview

This project analyzes food deserts and supermarket accessibility in Wake County, NC. The goals are to identify areas underserved by supermarkets, evaluate the demographics of residents in these areas, and recommend an optimal location for a new USDA-funded supermarket.

## Data Sources

* **Shapefiles**:

  * `orange_durham_wake_block_groups.shp` – Original block group boundaries
  * `wake_county.shp` – Wake County selection
  * `wake_county_NC_83.shp` – Wake County projected shapefile
  * `one_mile_buffer_intersection_NC_83.shp` – Areas within 1 mile of supermarkets
  * `food_deserts_wake_county.shp` – Areas outside 1-mile buffer
  * `2_mile_buffer_intersection.shp` – Areas within 2 miles of supermarkets
  * `new_food_deserts.shp` – Areas outside 2-mile buffer
* **Census Data**: `triangle_census.csv` – Population, household income, and vehicle ownership

## Methodology

1. **Food Desert Identification (1-mile criterion)**

   * Selected Wake County from the block group shapefile (COUNTYFP = 183).
   * Created a 1-mile buffer around supermarkets to define non-food desert areas.
   * Used intersection and symmetrical difference tools to isolate food desert areas.
   * Joined census data to calculate population and household characteristics.

2. **Demographic Analysis**

   * Population in 1-mile food deserts: **906,882 / 1,069,079 ≈ 84.83%** of residents.
   * Household characteristics:

     | Metric                    | Food Deserts | Wake County Overall |
     | ------------------------- | ------------ | ------------------- |
     | Zero-vehicle households   | 3.40%        | 3.97%               |
     | Income < \$35k households | 17.64%       | 18.80%              |
   * Conclusion: Residents in food deserts are not more likely to be poor or lack vehicles than county-wide residents.

3. **Supermarket Placement Recommendation** 🛒

   * Added fields: `zero_vehicles_percentage` and `less_than_35k_percentage`.
   * Created choropleth maps to visualize high-need areas.
   * Recommended location chosen where both percentages are high to maximize accessibility.

4. **Two-Mile Criterion Analysis**

   * Created 2-mile buffer and derived new food desert areas.
   * Population in 2-mile food deserts: **400,285 / 1,069,079 ≈ 37.44%**.
   * Household characteristics:

     | Metric                    | New Food Deserts | Wake County Overall |
     | ------------------------- | ---------------- | ------------------- |
     | Zero-vehicle households   | 2.29%            | 3.97%               |
     | Income < \$35k households | 15.95%           | 18.80%              |
   * Conclusion: A 2-mile criterion reduces the identified food desert population. The 1-mile criterion better targets underserved residents.

5. **Supermarket Placement (2-mile analysis)**

   * Same methodology as 1-mile analysis.
   * Optimal location remains consistent with 1-mile analysis, prioritizing high-need households.

## Maps & Visualization

* 1-mile and 2-mile food desert areas
* Choropleth maps:

  * Zero-vehicles percentage
  * Less than \$35k income percentage
* Comparison map of 1-mile vs. 2-mile food deserts

## Tools & Software

* **QGIS** – Buffer, Intersection, Symmetrical Difference
* **Vector Analysis** – Population, household income, vehicle ownership
* Choropleth mapping with Equal Count (quantile) classification

## Key Findings

* 1-mile food deserts cover **84.83%** of the population; 2-mile food deserts cover **37.44%**
* Residents in food deserts are slightly better off than county average in income and vehicle access
* Recommended supermarket location targets households with high need for access
* 1-mile criterion more effective at identifying underserved populations

