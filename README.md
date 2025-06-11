# next-location-prediction-ml

This project predicts the next geographic location of a user based on their movement trajectory using machine learning. It leverages the [Geolife Trajectories 1.3 Dataset](https://www.microsoft.com/en-us/download/details.aspx?id=52367) and Random Forest regression to forecast the user's upcoming latitude and longitude from temporal and spatial patterns.

---

## 🚀 Features

- Predicts the next latitude and longitude from past trajectory.
- Preprocesses `.plt` files from Geolife GPS data.
- Extracts and engineers features like hour of day, direction, distance, etc.
- Trains separate models for latitude and longitude prediction using ensemble methods.
- Supports custom input for next location prediction.
- Visualizes actual vs predicted locations using scatter plots.

---



🧠 Model Overview
Model Type: RandomForestRegressor (two separate models for latitude and longitude).

Features:
Spatial: dist_from_center, angle_from_center
Temporal: hour, hour_sin, hour_cos
