# next-location-prediction-ml

This project predicts the next geographic location of a user based on their movement trajectory using machine learning. It leverages the [Geolife Trajectories 1.3 Dataset](https://www.microsoft.com/en-us/download/details.aspx?id=52367) and Random Forest regression to forecast the user's upcoming latitude and longitude from temporal and spatial patterns.

---

##  Project Overview
This project aims to predict the next GPS location (latitude and longitude) of a user based on their movement history using classical machine learning techniques. It uses the Geolife Trajectories 1.3 Dataset by Microsoft Research, which consists of real-world GPS trajectory data collected from 182 users over five years. From this dataset we use data of 40 users to build this project.

##  Features

- Predicts the next latitude and longitude from past trajectory.
- Preprocesses `.plt` files from Geolife GPS data.
- Extracts and engineers features like hour of day, direction, distance, etc.
- Trains separate models for latitude and longitude prediction using ensemble methods.
- Supports custom input for next location prediction.
- Visualizes actual vs predicted locations using scatter plots.

---

## Applications : 
-  Location-based recommendations and services
-  Traffic and mobility pattern analysis
-  Smart navigation and route prediction
-  Urban planning and crowd flow modeling

##  Project Pipeline
### 1. Data Extraction & Preprocessing
- Extract .plt trajectory files.

- Parse them into a structured format using pandas.

- Generate timestamps and derive temporal features like hour, weekday, etc.

### 2. Feature Engineering
- Temporal Features: hour, hour_sin, hour_cos (to capture time-of-day cycles)

- Spatial Features: distance from center (Euclidean distance from trajectory centroid), angle from center (directional component)

- Target Variables: next latitude and next longitude generated using a one-step time shift (.shift(-1))

### 3. Data Cleaning & Noise Injection
- Drop rows with missing target values.

- Add Gaussian noise to latitude and longitude to: Simulate GPS imprecision, Reduce model overfitting, Round coordinates to 3 decimal places for generalization.

### 4. Modeling
- Use two separate RandomForestRegressor models: One for predicting the next latitude and another for predicting the next longitude
- Apply GridSearchCV with 5-fold cross-validation for hyperparameter tuning.
- Use a StandardScaler to normalize input features.

### 5. Evaluation
- Metrics: R² Score, RMSE (Root Mean Squared Error)

- Visualization: Scatter plots of actual vs predicted coordinates

- Feature importance rankings

### 6. Custom Input Prediction
- Accept user-defined current location and hour.

- Predict the next GPS coordinate using trained models.

##  Why Random Forest?
- Handles non-linear relationships in spatial-temporal data.

- Robust to overfitting when regularized properly.

- Provides feature importance insights for interpretability.

- Easy to tune with cross-validation.


