****# Bangalore Home Prices Prediction

## 📊 Project Overview

This project is a comprehensive end-to-end data science regression workflow for predicting residential property prices in Bangalore, India. The workflow demonstrates the entire process from data inspection and cleaning, through feature engineering and outlier removal, to model building and evaluation. It also covers exporting the trained model and necessary metadata for deployment.

---

### Key Steps & Features

- **Data Loading & Exploration**
  - Loaded a public Bangalore house price dataset.
  - Explored features such as area type, location, size, sqft, bathrooms, and price; cleaned irrelevant columns.

- **Data Cleaning & Feature Engineering**
  - Handled missing values and inconsistent data cases.
  - Extracted relevant features, such as the number of bedrooms (BHK).
  - Converted total square foot values to a consistent numerical format (averaging ranges and removing non-standard units).
  - Created additional features like `price_per_sqft`.

- **Dimensionality Reduction**
  - Reduced the number of location categories by grouping rare locations as "other" to simplify modeling and prevent overfitting.

- **Outlier Removal**  
  Used both:
  - **Domain/business rules:** e.g., minimum 300 sqft per BHK.
  - **Statistical analysis:** e.g., removing properties with price-per-sqft outside one standard deviation for their location.
  - Removed listings where higher BHKs have a lower unit price than smaller units in the same location.
  - Further removed properties with an abnormally high number of bathrooms.

- **Feature Encoding**
  - Applied one-hot encoding to the location categorical variable for compatibility with machine learning algorithms.

- **Modeling & Evaluation**
  - Trained a Linear Regression model as a baseline and compared it with Lasso and Decision Tree regressors via GridSearchCV.
  - Evaluated using K-Fold cross-validation, selecting the model with best generalization performance.

- **Prediction Function**
  - Developed a function to predict home price given user inputs (location, square feet, BHK, bathrooms), illustrating it with several example cases.

- **Deployment Preparation**
  - Exported the trained model as a pickle file.
  - Saved column metadata as a JSON file for later use in web/API deployment.
  
---

### 🚀 Technologies Used

- **Python**: Data cleaning, analysis, visualization, machine learning
- **Pandas, NumPy, Matplotlib**: Data manipulation and plotting
- **scikit-learn**: Machine learning modeling, cross-validation, and hyperparameter tuning
- **Pickle, JSON**: Model and config export for deployment

### 📂 Files in This Repository

- **banglore_home_prices_final project in cass.ipynb**: The complete Jupyter notebook including step-by-step code, comments, and plots.
- **bhp.csv**: (Intermediate data) Engineered/cleaned dataset.
- **banglore_home_prices_model.pickle**: Trained regression model.
- **columns.json**: Metadata containing column/encoding information for deployment.

---

## ⚡ Results

- Achieved high prediction accuracy (R² ≈ 0.85-0.86) on test data using cross-validation.
- Outlier removal and smart feature engineering significantly improved model reliability.
- The final workflow and model are ready for deployment in a Flask app or similar API for live price prediction scenarios.

