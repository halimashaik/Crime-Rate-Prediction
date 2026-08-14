# Crime Data Forecasting & Hotspot Detection

A machine learning and data analytics application that analyzes historical crime data in India, forecasts future crime trends, and visualizes crime patterns and potential hotspots.

The project uses **Recursive Support Vector Regression (SVR)** to forecast crime trends for the years **2024–2030** and provides interactive visualizations through a Streamlit dashboard.

## Demo Link

**Live Demo:** Coming soon.

> A live Streamlit deployment link will be added once the dashboard is publicly hosted.

## Table of Contents

- [Business Understanding](#business-understanding)
- [Data Understanding](#data-understanding)
- [Screenshots of Visualizations/Results](#screenshots-of-visualizationsresults)
- [Technologies](#technologies)
- [Setup](#setup)
- [Approach](#approach)
- [Status](#status)
- [Credits](#credits)

## Business Understanding

Crime is an important public-safety issue, and analyzing historical crime patterns can help identify trends across different states and crime categories.

The main goal of this project is to build a data-driven system that can:

- Analyze historical crime trends in India.
- Understand state-wise and category-wise crime patterns.
- Forecast future crime trends using machine learning.
- Identify areas with potentially higher crime activity.
- Visualize historical and predicted crime patterns.
- Provide an interactive dashboard for exploring the results.

The project combines **data preprocessing, feature engineering, machine learning, forecasting, geographical visualization, and interactive dashboards** into a single application.

### Challenges

Some of the main challenges encountered during the project include:

- Cleaning and standardizing crime data.
- Preparing historical crime records for machine learning.
- Handling categorical variables such as states and crime categories.
- Creating lag features for forecasting.
- Generating recursive future predictions.
- Combining prediction results with geographical data.
- Communicating the uncertainty of long-term forecasts.

## Data Understanding

The project uses historical crime data from India, including data sourced from the Indian Crimes Dataset and NCRB-related crime statistics.

### Dataset

The primary dataset used in the project is:

**Indian Crimes Dataset**

Source:

- [Kaggle – Indian Crimes Dataset](https://www.kaggle.com/datasets/sudhanvahg/indian-crimes-dataset)

The model is trained using historical data from **2020–2023**.

### Data Processing

The raw data is cleaned and transformed before being used for analysis and machine learning.

The workflow includes:

- Data cleaning.
- Handling missing or inconsistent values.
- Standardizing crime categories.
- Encoding categorical variables.
- Creating lag features.
- Preparing historical crime records for forecasting.
- Generating processed datasets for model training.

Processed datasets are stored in:

```text
data/processed/

Geographical Data

The project also uses Indian state-level GeoJSON data to create geographical crime visualizations.

Sources include:

GeoJSON – geohacker/india
GeoJSON – udit-001/india-maps-data

The cleaned geographical data is stored in:

json/cleaned.geojson
Forecasting Period

The model uses historical data from 2020–2023 to forecast future crime trends from 2024 to 2030.

The 2024 predictions are closer to the historical training period, while predictions further into the future become increasingly uncertain.

Forecasting Limitation

The forecasting model uses lag features, which represent information from previous periods.

For long-term forecasting, the model uses its own previous predictions as inputs for subsequent predictions. This is known as recursive forecasting.

Therefore:

Predictions closer to 2024 are more closely connected to observed historical data.
Predictions for later years such as 2026–2030 carry greater uncertainty.
The application displays a warning when users explore longer-term forecasts.

This limitation should be considered when interpreting the model's predictions.

Screenshots of Visualizations/Results
Crime Prediction

Crime Analysis Dashboard

Future Predictions

Crime Heatmap

Long-Term Forecast

Geographical Crime Map

Prediction Dashboard

State-Wise Crime Dashboard

Technologies
Programming Language
Python
Data Processing and Analysis
Pandas
NumPy
Machine Learning
Scikit-learn
Support Vector Regression (SVR)
Visualization
Matplotlib
Seaborn
Plotly
Geographical Visualization
GeoJSON
Interactive geographical maps
State-wise crime visualization
Dashboard
Streamlit
Development Tools
Jupyter Notebook
Visual Studio Code
Python virtual environment
Setup
Project Structure
crime_forecasting/
├── app/
│   └── visualization.py
├── data/
│   ├── raw/
│   └── processed/
├── json/
│   ├── india_state.geojson
│   └── cleaned.geojson
├── models/
├── notebooks/
│   ├── data_viewer.ipynb
│   ├── forecast_model.ipynb
│   └── preprocesing.ipynb
├── screenshots/
├── dsi.py
├── requirements.txt
├── run_project.ps1
└── README.md
Prerequisites

Make sure the following are installed:

Python 3.x
Git
PowerShell
Jupyter Notebook or Visual Studio Code
Running Project — Automated Script
Open PowerShell in the project root folder.
Run the automated setup script:
.\run_project.ps1
Manual Setup
1. Install Dependencies

Install the required Python packages:

pip install -r requirements.txt
2. Download and Clean Data

Run:

python dsi.py

This prepares the data required for the analysis and forecasting workflow.

3. Explore the Data

Run:

notebooks/data_viewer.ipynb

This notebook can be used to inspect and understand the available crime data.

4. Process the Data

Run:

notebooks/preprocesing.ipynb

This notebook cleans and prepares the data and generates the processed datasets required for the forecasting workflow.

5. Generate Data and Models

Run:

notebooks/forecast_model.ipynb

This notebook:

Creates forecasting features.
Trains the SVR model.
Generates future predictions.
Saves the trained models.
Generates prediction datasets.
6. Launch Dashboard

Navigate to the application directory:

cd app

Then run:

streamlit run visualization.py

The Streamlit dashboard will open in your browser.

Approach

The project follows a complete data analytics and machine learning workflow.

1. Data Collection

Historical crime data from India was collected from publicly available datasets, including the Indian Crimes Dataset.

2. Data Exploration

The collected data was examined to understand:

Crime categories.
State-wise crime patterns.
Historical trends.
Available years.
Data quality.
Distribution of crime records.

The data_viewer.ipynb notebook supports this stage.

3. Data Cleaning and Preprocessing

The raw data is cleaned and transformed into a format suitable for analysis and machine learning.

This includes:

Handling missing or inconsistent values.
Standardizing crime categories.
Preparing state information.
Cleaning crime records.
Creating structured datasets.

This process is implemented in:

notebooks/preprocesing.ipynb
4. Feature Engineering

The forecasting model uses lag features to incorporate information from previous periods.

These historical features allow the model to learn relationships between previous crime activity and future crime values.

5. Machine Learning Model

The project uses Support Vector Regression (SVR) to model and forecast crime trends.

The trained model and encoders are stored in:

models/

The project includes:

models/crime_encoder.pkl
models/state_encoder.pkl
models/svr_model.pkl
6. Recursive Forecasting

The system generates future predictions for crime trends from 2024 to 2030.

The forecasting process works recursively:

Historical Data
      ↓
Data Preprocessing
      ↓
Feature Engineering
      ↓
SVR Model
      ↓
Future Prediction
      ↓
Prediction becomes input
      ↓
Next Future Prediction
      ↓
Continue through 2030

Because future predictions are used as inputs for later predictions, uncertainty increases as the forecasting period becomes longer.

7. Geographical Analysis

GeoJSON data is combined with crime information to visualize state-level crime patterns.

The geographical analysis helps identify:

State-wise crime activity.
Crime concentration.
Potential hotspots.
Geographical patterns.
8. Visualization

The project uses multiple visualization techniques, including:

Crime trend charts.
Crime heatmaps.
Future prediction graphs.
Long-term forecasts.
State-wise comparisons.
Interactive geographical maps.
9. Interactive Dashboard

The final results are presented through a Streamlit dashboard.

The dashboard allows users to interactively explore crime patterns, historical trends, geographical information, and future predictions.

Status

Status: Completed

The project currently includes:

Historical crime data analysis.
Data preprocessing.
Feature engineering.
Lag-based forecasting.
SVR-based crime prediction.
Recursive forecasting from 2024–2030.
State-wise crime analysis.
Crime heatmaps.
Geographical crime visualization.
Interactive Streamlit dashboard.
Long-term forecast uncertainty warnings.
Future Improvements

Possible future improvements include:

Adding newer NCRB datasets.
Adding district-level crime forecasting.
Comparing SVR with other machine learning and time-series models.
Hyperparameter tuning.
Adding population data for per-capita crime rates.
Incorporating socioeconomic indicators.
Automating dataset updates.
Improving long-term forecasting reliability.
Deploying the Streamlit dashboard publicly.
Adding confidence intervals to future predictions.
Credits
Dataset

Indian Crimes Dataset – Kaggle

https://www.kaggle.com/datasets/sudhanvahg/indian-crimes-dataset

Geographical Data
geohacker/india
udit-001/india-maps-data
Libraries and Frameworks
Python
Pandas
NumPy
Scikit-learn
Matplotlib
Seaborn
Plotly
Streamlit

This project was developed as a data analytics and machine learning project focused on crime forecasting, hotspot detection, and interactive geographical visualization.