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

🧭 Project Overview
This project focuses on predicting a user's next GPS location (latitude and longitude) based on their current trajectory data using classical machine learning models. It utilizes the Geolife Trajectories 1.3 dataset released by Microsoft Research, which contains real-world GPS traces collected over five years from 182 users in Beijing.

The objective is to build a robust model that, given a user's current spatial and temporal information, can accurately forecast the next point in their movement path. This has practical applications in:

Location-based services (e.g., app recommendations, smart notifications)

Traffic pattern analysis

Human mobility modeling

Urban planning and smart navigation systems

📌 Key Steps in the Pipeline
Data Extraction & Parsing

Extract .plt files from the Geolife dataset.

Parse them into structured DataFrames (latitude, longitude, timestamp).

Feature Engineering

Temporal features: hour of day, weekday, hour_sin, hour_cos (to model cyclic patterns).

Spatial features:

Distance from center of user’s trajectory

Angle from center (bearing-like feature)

The raw latitude/longitude is not directly used in the model to prevent overfitting.

Target Variable Generation

The next point’s latitude and longitude are calculated using .shift(-1) on the sequence, turning it into a supervised learning problem (current → next).

Noise Injection & Overfitting Reduction

Added Gaussian noise to reduce overfitting on identical GPS points.

Used reduced coordinate precision (rounding) to simulate real-world GPS variation.

Model Training

Trained separate RandomForestRegressor models for predicting:

Next Latitude

Next Longitude

Used GridSearchCV with 5-fold cross-validation to optimize hyperparameters.

Evaluation Metrics

R² Score

RMSE (Root Mean Squared Error)

Feature Importance visualizations

Scatter plots comparing actual vs predicted locations

Custom Input Prediction

User can input a location and time (hour) and the model returns a predicted next GPS coordinate.

📍 Why Random Forest?
Random Forest was chosen because:

It handles non-linear spatial and temporal relationships well.

It provides interpretability (via feature importance).

It helps reduce overfitting via bagging and regularization.


