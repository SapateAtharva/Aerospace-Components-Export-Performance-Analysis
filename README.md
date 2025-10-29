India Aerospace Components Export Analysis (2019–2023)

This project analyzes the quarterly export performance of various aerospace components from India between Q1 2019 and Q4 2023. Using a synthetic dataset designed to mimic real-world data issues (missing values, inconsistent formatting), it applies a full data science pipeline including data cleaning, preprocessing, exploratory data analysis (EDA), and time-series forecasting.
The primary objectives are to identify export trends, understand key drivers, evaluate model performance, and forecast future annual export values using Linear Regression.

1. Introduction
India's aerospace sector has shown significant growth, with exports playing an increasingly important role. Analyzing component-level export data helps to understand market dynamics, identify high-performing segments, and inform strategic decisions for policymakers and industry stakeholders.
This project demonstrates a practical approach to handling and analyzing time-series export data, even when faced with real-world data imperfections.

2. Problem Statement
The main objective is to analyze and forecast the export trends of aerospace components from India using quarterly data from 2019 to 2023.
Key Questions


What are the overall and component-specific export trends over the period?


Which components contribute most significantly to total export value?


How can we clean and preprocess imperfect real-world data for analysis?


Can we build a simple regression model to forecast future annual export trends?


What are the limitations of the current model and potential areas for future work?



3. Dataset
Source: Synthetic CSV dataset (aerospace_exports_dirty.csv), loaded directly from a GitHub repository.
Structure
ColumnDescriptionYear_QuarterTime period (e.g., 2019-Q1)ComponentAerospace component type (string; inconsistent formatting possible)ExportValue_USD_MillionsExport value in millions of USDGov_Incentive_MillionsGovernment incentive in millions of USD
Data Quality Issues
The dataset intentionally includes common data issues:


Malformed rows (e.g., incorrect Year_Quarter format)


Inconsistent component names (extra whitespace, varied capitalization)


Missing numeric values



4. Data Science Pipeline
4.1 ETL and Data Cleaning / Preprocessing
Implemented in project.py.
Steps:


Extraction: Load the CSV file using Pandas (on_bad_lines='skip').


Transformation and Cleaning:


Validate and filter rows based on correct Year_Quarter format (YYYY-QX).


Split Year_Quarter into separate Year and Quarter columns.


Clean Component names (trim whitespace, apply title case).


Convert numeric columns using pd.to_numeric(errors='coerce').


Impute missing values in numeric columns using the median.


Apply StandardScaler to create a normalized Gov_Incentive_Scaled column.




Loading: Store the cleaned data in a Pandas DataFrame. Print summaries such as shape, info, missing values, and descriptive statistics.



4.2 Exploratory Data Analysis (EDA)
Visualizations generated using Matplotlib and Seaborn are saved in the plots/ directory.
PlotDescriptionFilenameTotal Export Trend (Annual)Line plot showing total exports per yeartotal_export_trend.pngTotal Value by ComponentBar chart showing cumulative exports per componentcomponent_total_exports.pngComponent Trends (Annual)Multi-line plot showing component-wise yearly trendscomponent_yearly_trends.pngExport Share (Latest Year)Pie chart showing export share by component for 2023component_pie_chart_latest_year.pngExport Value DistributionBox plot of quarterly export values per componentcomponent_export_distribution.pngCorrelation HeatmapCorrelation between component exports and incentivescorrelation_heatmap_quarterly.png

4.3 Model Selection
Model: Linear Regression (sklearn.linear_model.LinearRegression)
Task: Forecasting annual total export trends.
Rationale: A simple, interpretable model capturing the primary linear trend in aggregated annual export data.
Features:


X = Year


y = Total Annual ExportValue_USD_Millions



4.4 Model Training and Evaluation
Data Aggregation: Quarterly data aggregated into annual totals.
DatasetYearsTraining2019–2022Test2023
Evaluation Metrics:


Mean Absolute Error (MAE)


Root Mean Squared Error (RMSE)


R² (not applicable for a single test data point)



4.5 Forecasting and Visualization


Retrain the model on full annual data (2019–2023).


Forecast exports for 2024 and 2025.


Plot includes:


Actual export values (scatter)


Fitted linear regression trend line (with R²)


Forecasted points for 2024 and 2025




Saved as: plots/final_forecast_plot_annual.png

5. How to Run
# Clone the repository
git clone https://github.com/SapateAtharva/Aerospace-Components-Export-Performance-Analysis.git
cd Aerospace-Components-Export-Performance-Analysis

# Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn

# Run the project
python project.py

Output


Console: Data summaries, cleaning steps, model evaluation results, and forecasts.


Plots: Saved in the plots/ directory.



6. Conclusion
The analysis successfully cleans and processes the synthetic aerospace export dataset, revealing a consistent positive trend in India's aerospace exports between 2019 and 2023.
The Linear Regression model provides a solid baseline forecast, indicating continued export growth through 2024 and 2025. EDA results highlight component-level performance and contribution patterns across the analyzed years.

7. Future Work


More Data: Integrate real-world export datasets with destination countries and detailed component categories.


Advanced Models: Implement ARIMA, SARIMA, or Prophet to capture seasonality and non-linear patterns.


External Factors: Incorporate macroeconomic indicators such as GDP growth, trade policy changes, and global demand metrics.


Error Analysis: Conduct detailed residual analysis for better model interpretation.



8. Literature Review / References


Gupta, R., et al. (2020). Time Series Analysis of Aerospace Exports. Stratview Research Report.


Jain, A., & Banerjee, M. (2021). ARIMA Modeling Applications in Export Forecasting. Journal of Indian Economic Studies.


Singh, V., et al. (2023). Impact of Export Incentives on Trade Performance. Asian Journal of Trade and Economics.
(Additional references from 22070521165_Atharva_Sapate.docx can be included here.)



9. Summary
This project demonstrates a complete data science workflow — from raw data cleaning to visualization and forecasting — providing actionable insights into India's aerospace component exports and establishing a foundation for future, more advanced time-series modeling.

Would you like me to include a short “Project Structure” section (showing the folder layout like /data, /plots, /src, etc.) at the top before the “Abstract”? It’s a common best practice for GitHub repos.
