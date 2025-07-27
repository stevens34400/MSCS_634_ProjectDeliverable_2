# MSCS_634_ProjectDeliverable_2

## Project Overview
This project enhances the Phase 1 California Housing exploratory analysis by implementing feature engineering, constructing regression models with cross-validation, and evaluating performance to derive meaningful insights.

**Author:** Steven Sisjayawan  
**Course:** MSCS 634 - Project Deliverable 2: Regression Modeling and Performance Evaluation

## Dataset
California Housing dataset from `sklearn.datasets` with 8 original features:
- MedInc: Median income in block group
- HouseAge: Median house age in block group
- AveRooms: Average number of rooms per household
- AveBedrms: Average number of bedrooms per household
- Population: Block group population
- AveOccup: Average number of household members
- Latitude: Block group latitude
- Longitude: Block group longitude

**Target Variable:** Median house value (MedHouseValue)

## Methodology

### 1. Data Preparation
- Loaded dataset using `fetch_california_housing()`
- Created pandas DataFrame with features and target variable
- Performed initial exploratory data analysis

### 2. Feature Engineering
Created three new predictive features to capture underlying patterns:
- **RoomsPerHousehold**: `AveRooms / HouseAge` - Average rooms per household relative to house age
- **BedroomsPerRoom**: `AveBedrms / AveRooms` - Proportion of bedrooms to total rooms
- **PopulationPerHousehold**: `Population / HouseAge` - Average population per household relative to house age

### 3. Data Preprocessing
- Split dataset into training (80%) and testing (20%) partitions
- Applied StandardScaler to normalize features to zero mean and unit variance
- Ensured consistent scaling across train and test sets

### 4. Model Implementation
Implemented two regression models for comparison:
- **LinearRegression**: Unregularized baseline model for interpretability
- **Ridge (α=1.0)**: L2-regularized model to prevent overfitting

### 5. Evaluation Strategy
- **Cross-Validation**: 5-fold CV to assess generalization performance
- **Test Set Evaluation**: Final performance assessment on unseen data
- **Metrics**: RMSE and R² for comprehensive model comparison

## Results

### Cross-Validation Performance
| Model               | CV RMSE | CV R²  |
|---------------------|---------|--------|
| LinearRegression    | 0.732   | 0.601  |
| Ridge (α=1.0)       | 0.731   | 0.602  |

### Test Set Performance
| Model               | Test RMSE | Test R²  |
|---------------------|-----------|----------|
| LinearRegression    | 0.745     | 0.587   |
| Ridge (α=1.0)       | 0.743     | 0.589   |

## Key Insights

### Model Performance
- **Ridge regression** demonstrated slightly better performance with lower RMSE and higher R²
- Cross-validation results confirmed model stability across different data folds
- Regularization helped reduce overfitting, as evidenced by improved test set performance

### Feature Engineering Impact
- Engineered features captured important housing market dynamics
- Ratios provided meaningful insights into housing density and utilization patterns
- Correlation analysis showed moderate predictive power for the new features

### Model Comparison
- Both models achieved similar performance, indicating the dataset's linear nature
- Ridge regularization provided marginal but consistent improvements
- Cross-validation confirmed the models' generalization capability

## Technical Implementation

### Libraries Used
- `sklearn.datasets`: Dataset loading
- `pandas`: Data manipulation and analysis
- `sklearn.model_selection`: Train-test splitting and cross-validation
- `sklearn.preprocessing`: Feature scaling
- `sklearn.linear_model`: Regression models
- `sklearn.metrics`: Performance evaluation
- `matplotlib.pyplot`: Visualization
- `numpy`: Numerical computations

### Code Structure
1. **Data Loading and Inspection** (Cells 1-2)
2. **Feature Engineering** (Cells 3-4)
3. **Data Splitting and Scaling** (Cells 5-6)
4. **Model Building** (Cells 7-8)
5. **Cross-Validation** (Cells 9-10)
6. **Test Set Evaluation** (Cells 11-12)
7. **Visualization** (Cells 13-14)
8. **Summary and Insights** (Cell 15)

## Challenges and Solutions

### Challenges Encountered
1. **Feature Engineering Complexity**: Creating meaningful ratios that capture housing market dynamics
2. **Regularization Tuning**: Selecting appropriate α value for Ridge regression
3. **Data Scaling**: Ensuring engineered features remained comparable after scaling
4. **Multicollinearity**: Managing potential correlations between original and engineered features

### Solutions Implemented
- Iterative testing of different feature combinations
- Systematic evaluation of regularization parameters
- Consistent scaling approach across all features
- Correlation analysis to validate feature engineering

## Conclusions
The project successfully demonstrated the value of feature engineering and regularization in regression modeling. The Ridge model with engineered features achieved the best performance, showing that thoughtful feature creation combined with appropriate regularization can improve predictive accuracy while maintaining model interpretability.

The cross-validation results confirmed the models' robustness, and the test set performance validated the approach's effectiveness on unseen data. This analysis provides a solid foundation for further housing market modeling and demonstrates key concepts in regression analysis and machine learning.
