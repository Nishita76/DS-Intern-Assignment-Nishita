# **Energy Consumption Analysis and Prediction Report**

#### Author: Nishita <br> Organization: SmartManufacture Inc. <br> Date: 10 May 2025

## Problem Overview

The manufacturing client of SmartManufacture Inc. is facing rising energy costs and seeks a data-driven solution to better manage their equipment's energy consumption. As a data scientist, my role was to analyze historical sensor data and develop a predictive model for equipment energy consumption based on various environmental factors within the facility.

## Objective
- Understand how environmental and operational parameters affect equipment energy usage.
- Develop a robust regression model to predict equipment energy consumption.
- Evaluate and compare model performances.
- Deliver actionable insights to optimize energy use.

## Dataset Overview
The dataset consists of timestamped sensor readings from a manufacturing facility, including:

- Energy usage:
equipment_energy_consumption (target)
lighting_energy
- Environmental readings:
Temperatures and humidity from 9 facility zones
Outdoor temperature, humidity, wind speed, pressure, etc.
- Engineered time features:
hour, dayofweek, month
- Additional:
random_variable1, random_variable2 (purposefully ambiguous to test feature selection skills)

## Approach to the Problem
The goal of this project was to analyze energy consumption patterns and build a model to predict future equipment energy usage, helping organizations reduce energy costs and improve operational efficiency.

We followed a structured data science workflow:


1. **Data Cleaning and Preparation:**
- Handled missing values and ensured consistent formatting.
- Removed unnecessary columns.
- Normalized and encoded data where required.

2. **Exploratory Data Analysis (EDA):**
- Visualized energy usage patterns by hour and zone.
- Investigated temperature trends and operational loads.
- Identified correlation between input features and energy consumption.

3. **Model Building and Evaluation:**
- Applied multiple regression models, with Random Forest performing best.
- Hyperparameter tuning was attempted using GridSearchCV.
- Evaluated models based on RMSE, MAE, and R² score.



## Key Insights from the Data
Through in-depth data exploration and visualization, it uncovered several important patterns and anomalies in equipment energy consumption:

1. Time-Based Usage Patterns
- Hour of the Day emerged as the most significant feature influencing energy usage.
- Energy consumption consistently peaked between 7 PM and 8 PM, slightly outside typical working hours.
- During late-night hours (post 9 PM), energy usage dropped sharply, revealing potential to automate shutdowns and reduce idle energy consumption.

2. Zone-Level Observations
- Zone 8 Temperature had the second-highest influence on energy consumption, suggesting this area might be poorly ventilated, overused, or house energy-intensive equipment.
- Some zones like Zone 3 and Zone 6 displayed steady consumption irrespective of temperature changes, hinting at fixed-load equipment or inefficiencies.

3. Outliers and Anomalies
- Boxplots and distribution plots revealed spikes in energy usage that didn’t align with expected patterns.
- These outliers may represent manual overrides, equipment malfunctions, or unusual activity.
- After removing outliers, model performance improved, indicating that these extreme values were likely noise or non-repeatable behaviors.

4. Random Variables in the Data
- The dataset included two randomly generated variables, as confirmed through correlation analysis and importance scores.
- These variables showed no meaningful relationship with energy consumption, and their inclusion initially confused the model.
- After identifying and removing them, the model performance significantly improved, highlighting the importance of data cleaning and feature relevance in machine learning.

5. Correlation and Relationships
- A strong relationship was found between hourly patterns and energy usage, validating the focus on time-based features.
- Some temperature-related features showed weaker correlations, but a few still contributed to predictive performance.
- Pair plots and scatter plots helped confirm that energy consumption behavior was non-linear, reinforcing the use of non-linear models.

6. Visualization-Driven Findings
- Line plots showed consistent daily patterns and highlighted repeating trends across days.
- Scatter plots between features and energy usage illustrated non-linear relationships, justifying the selection of tree-based models like Random Forest over simpler methods.
- Hour of the Day emerged as the most significant feature influencing energy usage through feature importance plot.
- Visualizations made it easier to identify trends, outliers, and unusual peaks, supporting both modeling and practical recommendations.



## Model Performance Evaluation
We tested multiple machine learning models to predict energy consumption, beginning with simple models and gradually moving to more advanced techniques.

 1. Linear Regression (Baseline Model)

- We initially applied Linear Regression, a basic model that assumes a straight-line relationship between features and energy usage.
- However, the model performed poorly, with low accuracy and high error, because energy usage patterns were non-linear and complex.


2. Random Forest Regressor (Improved Model)

- We then implemented a Random Forest Regressor, a model made up of multiple decision trees.
- It handled non-linear relationships much better with 0.66 R² and provided a significant boost in prediction accuracy.
- The model captured the hourly energy patterns and was more robust to outliers and noise.

3. Hyperparameter Tuning

- To further improve the performance, we used RandomizedSearchCV to find the best settings (like number of trees, depth of trees, etc.).
- After tuning, the model achieved a little higher R² scores and lower Mean Squared Error (MSE) on the test data, indicating better generalization.

4. Final Performance
The final model used was a Random Forest Regressor, which is known for its reliability and interpretability.

- R² Score: 0.669
The model explains ~67% of the variability in energy consumption, which is a solid result for real-world forecasting.
- RMSE (Root Mean Squared Error): Reasonable level, indicating moderate prediction errors.
- MAE (Mean Absolute Error): Low enough to be actionable, confirming the model can provide useful estimates.

These metrics confirm that the model can reliably forecast energy usage trends, though it's not perfectly accurate due to complex real-world behaviors.

## Recommendations to Reduce Equipment Energy Consumption
Based on the analysis and model results, here are some actionable steps:

- Optimize Night-Time Energy Usage:
Implement automation to shut down or scale back non-essential equipment after peak hours (post 9 PM).

- Shift High-Load Activities:
If possible, reschedule energy-intensive operations to mid-day hours where energy demand is more stable and predictable.

- Use Predictive Scheduling:
Use this model to forecast high-demand periods and prepare accordingly, preventing unnecessary power use.

- Monitor Environmental Factors:
Track temperature and other variables to identify how they impact energy demand and adjust systems proactively.



## Practical Insights and Recommendations
- Monitoring dashboards can be built on top of this model to help managers and facility teams take quick decisions.
- Weekly reports could help track peak usage hours and spot abnormalities early.
- Energy budgeting can be more accurate with such forecasting tools in place.
- These insights are particularly useful for factories, offices, or smart buildings looking to reduce operational costs.

## Model Limitations
While our model gave useful predictions, there are some limitations:

🔹 Limited Features: <br>
The dataset did not include other important factors like equipment type, occupancy, or humidity, which could affect energy consumption. This limited the model's ability to fully explain some variations.

🔹 Random Variables: <br>
We found two randomly generated variables in the dataset. These didn’t contribute to the prediction and were removed. Including such irrelevant data can affect the model’s performance.

🔹 Time Dependence Ignored: <br>
Energy usage over time can be dependent on previous hours or days. Our model treated each row separately, so it may have missed such patterns. A time-series approach could improve this.

🔹 Interpretability: <br>
Random Forest gave better results than Linear Regression, but it’s not easy to explain how it makes predictions. For stakeholders, a simpler model might be easier to understand even if less accurate.

🔹 Outliers: <br>
Although we removed some outliers, a few still remained. These may have slightly impacted the model’s learning and could be handled better with more advanced techniques.


```python

```
