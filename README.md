# RideWise: Urban Bike Mobility Forecaster

![RideWise Badge](https://img.shields.io/badge/Status-Deployed-success?style=for-the-badge) ![Python Badge](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python) ![Streamlit](https://img.shields.io/badge/Streamlit-Framework-red?style=for-the-badge&logo=streamlit)

## 🚴‍♂️ Project Overview
RideWise is a machine learning-powered web application that forecasts daily bike-sharing demand in urban areas based on weather conditions, temporal variables (seasons, months, weekdays), and events/holidays. The tool provides actionable, interactive insights for urban planners and transit operators to optimize fleet distribution and predict ridership surges.

## ✨ Features
- **Predictive Demand Modeling**: Real-time evaluation of the expected number of bike rentals using multiple historical categorical and numerical features.
- **Explainable Analytics**: Provides a dynamic "Insight Report" that logically interprets the reasons behind the generated prediction (e.g., negative impacts of heavy rain or high humidity).
- **Stunning Interactive UI**: A fully interactive, responsive, and aesthetically pleasing web dashboard built with Streamlit, enabling users to test their own combinations for varying forecasting scenarios.

## 🧠 Machine Learning Models
This project explored several regression techniques—from baseline linear models to complex ensemble trees—extensively scoped out and evaluated with `GridSearchCV` to locate the supreme configuration.

### Tested Configurations & Performance (R² Scores)
| Model | Optimization State | R² Variance Captured | 
| ----- | ------------------ | -------------------- |
| **Linear Regression** | Baseline | `0.867` |
| **Random Forest Regressor** | Baseline | `0.892` |
| **Random Forest Regressor** | GridSearch Tuned | `0.894` |
| **Gradient Boosting Regressor** | Baseline | **`0.908`** |
| **Gradient Boosting Regressor** | GridSearch Tuned | `0.903` |

*The **Gradient Boosting Regressor** demonstrated the highest performance (achieving nearly a ~91% variance capture accuracy) and was uniquely serialized as the production model for the deployment pipeline.*

## 📂 Repository Structure
- `app.py`: The core Streamlit application file hosting the dynamic web dashboard.
- `Linear_regression.ipynb`: Jupyter Notebook documenting Data Engineering, Exploratory Data Analysis (EDA), and preliminary linear algorithms.
- `RandomForest,GradientBoosting.ipynb`: Advanced ensemble modeling notebook detailing exhaustive tree-based approaches and hyperparameter tuning paths.
- `Saved_model_files/`: Directory containing the exported serialized `gradient_boost.pkl` inference file alongside feature mappings (`feature_names.pkl`).
- `day.csv` & `preprocessed_day.csv`: The datasets utilized for model training.

## 🚀 Installation & Usage
1. Clone this repository to your local environment.
2. Install the necessary system dependencies via pip using `requirements.txt`:
```bash
pip install -r requirements.txt
```
3. Run the Streamlit application:
```bash
streamlit run app.py
```
*Open your browser and navigate to `http://localhost:8501` to view your dashboard!*

## 🏙️ Core Use Cases
- **Operational Fleet Rebalancing**: Anticipate surges or shortages natively by forecasting demand curves due to favorable or adverse conditions. 
- **Infrastructure Impact Assessment**: Researchers can evaluate how specific micro-characteristics (i.e. weather drops or holiday clustering) consistently impact ridership flows for better city planning.
