This project is designed to predict weather patterns in African countries using historical weather data. The goal is to forecast temperatures based on various factors such as location, date, humidity, wind speed, and precipitation. The project involves:

Preprocessing the dataset: Filtering, cleaning, and feature engineering.
Exploratory Data Analysis (EDA): Exploring temperature trends, weather conditions, and insights from various features.
Modeling: Training a Random Forest Regressor model to predict temperatures.
Evaluation: Using metrics like R-squared, Mean Squared Error (MSE), and Root Mean Squared Error (RMSE) to assess model performance.
Prediction Interface: Users can input a location and date to receive a temperature prediction.


Observation

Feature Engineering and Data Preparation

We removed columns that we deemed irrelevant for the prediction of temperature such as air quality, visibility, time-based features like sunrise/sunset, etc.
Remaining features are
Categorical: country, location_name, condition_text
Numerical: humidity, wind_kph, precip_mm, year, month, day
The target variable is temperature_celsius.
Date conversion: the last_updated column is converted to a datetime format, and new features like the year, month, and day are extracted.
Model Development

The categorical columns which are location_name, country and condition_text are one-hot encoded. This is necessary as machine learning models typically require numerical input, and one-hot encoding transforms categorical data into a binary matrix.
We used Random Forest Regressor, which is a robust model for regression tasks. Random forests typically perform well with diverse data and are less prone to overfitting, thus making it suitable for this kind of weather prediction task. Our model uses 100 estimators (n_estimators=100), and a random seed ensures reproducibility.
Evaluation Metrics

R-squared: The model has an R-squared value of 0.886, which is quite high. This indicates that the model explains about 88.6% of the variance in the temperature data, suggesting good predictive power.
Mean Squared Error (MSE): The MSE value is 2.65, indicating that, on average, the model's predictions are off by approximately 2.65 degrees Celsius squared.
Root Mean Squared Error (RMSE): The RMSE value is 1.63 degrees Celsius, which is a more interpretable measure of error. This means that, on average, the model's predictions are off by 1.63°C.
Temperature Prediction

The predict_weather function allows users to input a location and a date, and it uses the trained model to predict the temperature for that location on the given date. This function creates a feature vector based on the given location and date, along with average values for humidity, wind speed, and precipitation.
The code supports interactive input for location and date, and it also checks if the location exists in the training dataset (location_names), ensuring valid inputs.
Visualizing Temperature Trends

Predicted vs Actual Temperature

The scatter plot compares actual temperature measurements with model-predicted temperatures.
The close alignment of points along the red line indicates that the model predicts temperature accurately.
Deviations from the line are minimal, suggesting a reliable prediction model with minimal error.
Location-Specific Temperature Over Time

For each valid location entered, a line plot is shown, visualizing how the temperature has changed over time. This provides a clear visual representation of temperature trends at specific locations. The interactive plot updates after each prediction and renders immediately, allowing the user to see the data for each location.
Conclusion
This project provides a comprehensive solution for predicting weather patterns in African countries based on historical data. By preprocessing, analyzing, and modeling the data, users can gain insights into temperature trends and make predictions for specific locations and dates. The interactive system allows for quick temperature predictions, making it useful for anyone needing weather information for African locations.

Use Cases
Agriculture: farmers can use this system to predict temperature trends for different regions, helping with crop planning and protection from extreme weather.
Disaster management: authorities can predict temperature changes to issue timely warnings for heatwaves mitigating the effects of climate disasters.
Tourism: travelers can plan visits to specific regions based on weather forecasts, such as avoiding heatwaves.
Climate research: researchers can use it to study historical weather patterns in Africa, helping to model climate change and its regional effects.
Energy sector: energy providers can adjust their strategies based on temperature predictions, particularly for solar energy, which is weather-dependent.
Health: public health officials can monitor temperature trends to address heat-related illnesses and public health emergencies.
Logistics and supply chain: companies can optimize delivery schedules based on weather forecasts, particularly in regions where extreme temperatures may affect operations.
