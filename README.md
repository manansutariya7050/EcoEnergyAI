# EcoEnergy AI

## AI-Powered Smart Campus Energy Consumption Prediction and Optimization System

**1M1B AI for Sustainability Virtual Internship Project**

---

## 1. Project Overview

EcoEnergy AI is a machine-learning prototype designed to support energy-management decisions in educational campuses.

The project analyzes historical electricity consumption data, identifies patterns, predicts future electricity values, detects potentially unusual observations, and provides simple sustainability-oriented recommendations.

The system is intended to work as a **decision-support tool**. It does not automatically control electrical equipment.

## 2. Problem Statement

Educational campuses use electricity for classrooms, laboratories, computer systems, lighting, cooling, and other facilities. Understanding and planning electricity consumption can be difficult when historical data is only reviewed after the energy has been used.

Campus administrators and facility teams need a simple, data-driven way to understand past electricity consumption, estimate future demand, and identify unusual usage patterns.

EcoEnergy AI addresses this problem by using machine learning to analyze historical electricity data, identify consumption patterns, forecast future electricity values, and detect potential anomalies. The project demonstrates how AI-based forecasting can support better energy-management decisions and contribute to responsible energy use in educational institutions.

## 3. Sustainable Development Goal Alignment

### Primary SDG

**SDG 7: Affordable and Clean Energy**

EcoEnergy AI supports SDG 7 by demonstrating how AI and data analysis can be used to understand electricity consumption and support more responsible energy-management decisions.

### Related SDGs

- **SDG 11: Sustainable Cities and Communities** — supports resource-efficient institutions.
- **SDG 13: Climate Action** — may contribute to sustainability and climate-related efforts if energy consumption is reduced after implementation.

SDG 7 is the main focus of this project.

## 4. Main Objectives

- Analyze historical electricity consumption.
- Identify yearly and monthly consumption patterns.
- Prepare time-series data for machine learning.
- Create useful forecasting features.
- Train and compare machine-learning models.
- Forecast electricity consumption for the next 12 months.
- Identify potential unusual electricity observations.
- Provide simple energy-management recommendations.
- Demonstrate responsible and transparent use of AI.

## 5. Technologies Used

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Random Forest Regressor
- Gradient Boosting Regressor
- Time-Series Forecasting
- Feature Engineering
- Anomaly Detection
- Data Visualization

## 6. Dataset

The project uses the `Electric_Production.csv` dataset.

| Property | Value |
|---|---:|
| Number of records | 397 |
| Number of columns | 2 |
| Columns | `DATE`, `Value` |
| Frequency | Monthly |
| Start date | January 1985 |
| End date | January 2018 |
| Missing values | 0 |
| Duplicate rows | 0 |
| Mean value | 88.847218 |
| Standard deviation | 15.387834 |
| Minimum value | 55.315100 |
| Maximum value | 129.404800 |

### Dataset limitation

The dataset contains only dates and electricity values. It does not include actual campus information such as building-level consumption, occupancy, weather, temperature, HVAC usage, holidays, electricity tariffs, or appliance-level usage.

Therefore, this project is a forecasting prototype and should not be presented as a deployed campus energy system.

## 7. Project Workflow

1. Load the electricity dataset.
2. Convert the date column into date format.
3. Check missing values and duplicate rows.
4. Sort the data chronologically.
5. Explore historical, yearly, and monthly patterns.
6. Create time-series features.
7. Split the data into training and testing sets chronologically.
8. Train Random Forest and Gradient Boosting models.
9. Evaluate the models using MAE, RMSE, and R².
10. Select the better-performing model.
11. Generate a 12-month forecast.
12. Detect potential anomalies.
13. Generate sustainability-oriented recommendations.

## 8. Feature Engineering

The following features were created:

| Feature | Meaning |
|---|---|
| `Year` | Calendar year |
| `Month` | Month number |
| `Lag_1` | Previous month's electricity value |
| `Lag_2` | Electricity value from two months earlier |
| `Lag_3` | Electricity value from three months earlier |
| `Lag_6` | Electricity value from six months earlier |
| `Lag_12` | Electricity value from twelve months earlier |
| `Rolling_Mean_3` | Average of the previous three values |
| `Rolling_Mean_6` | Average of the previous six values |
| `Rolling_Mean_12` | Average of the previous twelve values |

Feature engineering reduced the usable dataset from 397 records to 385 records because earlier rows did not have enough previous observations to calculate all features.

## 9. Machine-Learning Models

### Random Forest

Random Forest combines multiple decision trees to produce a prediction. It can learn non-linear relationships between historical electricity values and the target value.

### Gradient Boosting

Gradient Boosting builds models sequentially. Each new model tries to reduce the errors made by earlier models.

Both models were trained and evaluated using a chronological train/test split.

## 10. Model Evaluation

The models were evaluated using:

- **MAE — Mean Absolute Error:** Average absolute prediction error. Lower is better.
- **RMSE — Root Mean Squared Error:** Gives more importance to larger errors. Lower is better.
- **R² Score:** Indicates how much variation in the target is explained by the model. Higher is better.

### Results

| Model | MAE | RMSE | R² Score |
|---|---:|---:|---:|
| Random Forest | 2.981245 | 4.127173 | 0.813956 |
| Gradient Boosting | 3.226218 | 4.288972 | 0.799083 |

**Selected model: Random Forest**

Random Forest was selected because it achieved lower MAE and RMSE and a higher R² score.

## 11. Future Forecast

The selected Random Forest model was used to estimate electricity values for the next 12 months, from February 2018 to January 2019.

| Month | Predicted Value |
|---|---:|
| February 2018 | 102.6172 |
| March 2018 | 101.2804 |
| April 2018 | 90.5540 |
| May 2018 | 91.6578 |
| June 2018 | 104.3042 |
| July 2018 | 113.2972 |
| August 2018 | 110.1450 |
| September 2018 | 99.8092 |
| October 2018 | 92.8534 |
| November 2018 | 98.8591 |
| December 2018 | 114.7395 |
| January 2019 | 116.5736 |

The average forecast is approximately **103.06**.

These are model estimates and are not guaranteed future measurements.

## 12. Anomaly Detection

Potential anomalies were identified by comparing actual test-period values with predicted values.

- Anomaly threshold: approximately **3.7274**
- Potential anomalies detected: **21**

A potential anomaly does not automatically mean that there is an equipment fault. It means that the actual value was unusually different from the model's expectation and should be investigated by a responsible person.

## 13. Sustainability Recommendations

- Review HVAC, lighting, laboratory equipment, and other energy-intensive systems during higher-demand periods.
- Use forecasts to plan energy-saving checks before expected high-demand periods.
- Investigate potential unusual electricity patterns.
- Compare future consumption with historical averages.
- Use the system as a support tool rather than an automatic control system.

## 14. Target Users

- Campus administrators
- Facility-management teams
- Energy-management teams
- Sustainability teams
- Educational institutions
- Students and staff interested in energy awareness

## 15. Responsible AI

### Fairness

The current dataset does not contain personal or demographic information. If future campus data includes multiple buildings or user groups, the data should be checked for missing or unbalanced representation.

### Transparency

The project explains the dataset, features, models, evaluation metrics, forecast results, and limitations. Predictions are presented as estimates rather than guaranteed outcomes.

### Ethics

Potential anomalies should be investigated before any operational decision is made. The system should not be used to make unsupported or harmful decisions.

### Privacy

The current dataset does not contain student, staff, or personal information. A future campus deployment should collect only necessary data and protect it appropriately.

## 16. Expected Impact

If implemented with actual campus energy-meter data, EcoEnergy AI could:

- Support better energy planning.
- Help identify high-demand periods.
- Highlight unusual consumption patterns.
- Improve sustainability awareness.
- Support energy-efficiency initiatives.
- Potentially reduce avoidable energy use and energy costs.

Actual cost savings, electricity reduction, and carbon-emission reduction have not been measured in the current prototype.

## 17. Limitations

- The dataset is not specific to a real campus.
- Only date and electricity value are available.
- Weather and occupancy information are not included.
- Building-level data is not included.
- Electricity tariff data is not included.
- Carbon-emission factors are not included.
- Forecast values may differ from actual future values.
- Anomaly alerts require human investigation.
- The prototype does not automatically control electrical equipment.

## 18. Future Scope

- Connect the system to real campus smart meters.
- Add building-level electricity data.
- Include weather and temperature data.
- Include occupancy and academic-calendar information.
- Add electricity tariff data.
- Estimate cost savings and carbon-emission reduction.
- Develop a web dashboard.
- Add alerts for high-demand periods.
- Compare additional forecasting models.
- Add human review for anomaly explanations.

## 19. Suggested Project Structure

```text
EcoEnergy-AI/
│
├── Electric_Production.csv
├── EcoEnergyAI.ipynb
├── README.md
│
├── visualizations/
    ├── historical_electricity_trend.png
    ├── yearly_average_trend.png
    ├── monthly_pattern.png
    ├── model_rmse_comparison.png
    ├── actual_vs_predicted.png
    ├── feature_importance.png
    ├── future_12_month_forecast.png
    └── anomaly_detection.png
```

## 20. How to Run the Project

1. Install Python.
2. Install Jupyter Notebook or use Google Colab.
3. Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

4. Place `Electric_Production.csv` in the same folder as the notebook.
5. Open `EcoEnergyAI.ipynb`.
6. Run the notebook cells in order.
7. Review the visualizations, model results, forecast, and anomaly detection output.

## 21. Conclusion

EcoEnergy AI demonstrates how machine learning can support sustainability-focused energy management. The project analyzes historical electricity data, identifies patterns, compares forecasting models, predicts future values, detects potential anomalies, and provides simple recommendations.

Random Forest performed better than Gradient Boosting in the current experiment. However, the project is still a prototype because the dataset is not campus-specific.

A future version using real campus energy-meter data and additional information such as weather, occupancy, and building usage could provide more useful and practical energy-management insights.