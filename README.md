# Used Car Price Analysis

## Objective
The goal of this project is to understand the factors that affect used car prices and provide actionable insights to a used car dealership for inventory optimization and pricing strategies.

## Dataset
The dataset is a subset of a Kaggle used car dataset containing information on 426,000 cars. Key columns include:
- `price`: Sale price of the car
- `year`: Year of manufacture
- `odometer`: Mileage
- `manufacturer`, `model`, `condition`, `fuel`, `transmission`, `drive`

## Data Preparation
1. Filtered unrealistic prices (`price > 100`) and missing values.
2. Feature engineering:
   - `car_age` = 2025 - `year`
   - `mileage_k` = `odometer` / 10,000
3. Dropped irrelevant columns (`description`, `posting_date`, `image_url`, etc.)
4. One-hot encoded categorical features.
5. Standardized numeric features (`odometer`, `car_age`, `mileage_k`).
6. Log-transformed `price` to reduce skewness.

## Exploratory Data Analysis (EDA)
- Price distribution is right-skewed; log transformation normalizes it.
- Higher car age and mileage reduce price.
- Cars in excellent condition or premium brands retain higher prices.
- Fuel type, transmission, and drive type influence pricing.
- Correlation heatmap shows strong negative correlation between `car_age`, `mileage_k` and price.

## Modeling
Several regression models were built and evaluated:

| Model                 | R² (Test) | RMSE  | MAE   | CV R² |
|-----------------------|------------|-------|-------|-------|
| Linear Regression     | 0.55       | 0.48  | 0.35  | 0.54  |
| Ridge                 | 0.56       | 0.47  | 0.34  | 0.55  |
| Lasso                 | 0.54       | 0.49  | 0.35  | 0.53  |
| Decision Tree         | 0.68       | 0.36  | 0.27  | 0.66  |
| Random Forest         | 0.78       | 0.30  | 0.22  | 0.77  |
| Gradient Boosting     | 0.79       | 0.29  | 0.21  | 0.78  |
| AdaBoost              | 0.74       | 0.32  | 0.24  | 0.73  |

**Key insight:** Random Forest and Gradient Boosting perform best capturing non-linear relationships and interactions.

## Feature Importance (Random Forest)
Top features impacting price:
1. `car_age`
2. `mileage_k`
3. `condition`
4. `manufacturer`
5. `fuel`

## Visualizations
- **Price vs. Odometer** colored by `condition`
- **Price vs. Car Age** grouped by `fuel type`
- **Manufacturer vs. Price** grouped by `transmission`
- **Year vs. Average Price** by `drive type`
- Predicted vs. Actual prices scatterplot

## Recommendations
1. **Inventory Strategy:**
   - Prioritize newer, low-mileage cars in excellent condition.
   - Stock premium and hybrid/electric vehicles.
2. **Pricing Guidance:**
   - Adjust prices based on age, mileage, and condition.
   - Use predictive model to set competitive prices.
3. **Regional Adjustments:**
   - AWD/4WD cars for snowy/mountain regions.
   - Fuel-efficient vehicles in urban/high-gas-price areas.

## Conclusion
Used car prices are driven primarily by car age, mileage, condition, and brand. By using predictive models and insights from feature importance, the dealership can optimize inventory and pricing to improve profitability and align with consumer demand.

