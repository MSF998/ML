# Bengaluru House Price Prediction 🏡

**A machine learning project to predict house prices in Bengaluru using Scikit-learn, demonstrating data cleaning, feature engineering, and model evaluation.**

---

![Project Banner](URL_TO_YOUR_PROJECT_BANNER_IMAGE)
_(Pro-tip: Create a simple, attractive banner using a free tool like Canva. It makes your project look incredibly professional. Upload the image to your GitHub repo and link to it here.)_

## 1. Problem Statement

The Bengaluru real estate market is notoriously dynamic and complex. The goal of this project is to build a machine learning model that can accurately predict the price of a house based on its key features (such as location, size, number of bathrooms, etc.). This model can help potential buyers and sellers make more informed decisions.

## 2. Tech Stack

- **Python:** 3.9
- **Libraries:**
  - **Pandas:** For data loading, manipulation, and cleaning.
  - **NumPy:** For numerical operations.
  - **Matplotlib & Seaborn:** For data visualization and exploratory analysis.
  - **Scikit-learn:** For data preprocessing, model training, and evaluation.
- **Environment:** Jupyter Notebook / VS Code

## 3. Setup and Installation

To run this project on your local machine, follow these steps:

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
    cd your-repo-name
    ```
2.  **Create a virtual environment:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```
3.  **Install the required libraries:**

    ```bash
    pip install -r requirements.txt
    ```

    _(Pro-tip: Create a `requirements.txt` file by running `pip freeze > requirements.txt` in your activated virtual environment. This is a professional best practice.)_

4.  **Launch the Jupyter Notebook:**
    ```bash
    jupyter notebook
    ```

## 4. Project Walkthrough

### 4.1. Data Loading and Initial Exploration

- The dataset was sourced from Kaggle and contains over 13,000 property listings.
- Initial exploration using `.describe()` revealed several key insights:
  - Missing values were present in the `bath` and `balcony` columns.
  - The `price` column showed a very high standard deviation, indicating a wide spread of prices.
  - Potential outliers were identified (e.g., a property with 40 bathrooms).

### 4.2. Data Cleaning and Feature Engineering

- **Handling Missing Values:** Missing bathroom values were filled using the median value for that location.
- **Outlier Removal:** Properties with an extreme number of bathrooms or an unrealistic price-per-square-foot were treated as outliers and removed to create a more robust model.
- **Feature Creation:** A new, highly informative feature, `price_per_sqft`, was created to better capture the value of a property. _(Note: This feature was used for analysis and outlier detection but was removed before training to prevent data leakage.)_
- **Categorical Encoding:** The `location` column, which is textual, was converted into numerical data using one-hot encoding so the model could understand it.

### 4.3. Key Visualizations

**(Embed 2-3 of your most insightful charts here. You can screenshot them from your notebook and add them to your repo.)**

**Price Distribution Histogram:**
![Price Distribution](URL_TO_YOUR_HISTOGRAM_IMAGE)
_This histogram shows the distribution of house prices after outlier removal. We can see it follows a more normal distribution._

**Price vs. Square Footage:**
![Price vs Sqft](URL_TO_YOUR_SCATTERPLOT_IMAGE)
_This scatter plot shows the clear positive correlation between the size of a property and its price._

## 5. Model Building and Evaluation

Three different regression models were trained and evaluated to find the best performer. The models were evaluated using the R-squared score and Root Mean Squared Error (RMSE) on the test set.

| Model                       | R-squared Score | RMSE (in Lakhs) |
| :-------------------------- | :-------------- | :-------------- |
| Linear Regression           | 0.48            | 115.15          |
| **Random Forest Regressor** | **0.65**        | **89.11**       |
| Gradient Boosting Regressor | 0.60            | 96.17           |

## 6. Conclusion

The **Random Forest Regressor** was the best-performing model, achieving an **R-squared score of 0.65** and an **RMSE of ₹89.11 Lakhs**.

This project successfully demonstrates a complete machine learning workflow, from raw data to a trained predictive model. Key takeaways include the critical importance of data cleaning and feature engineering in improving model performance. The final model can provide a reasonable estimate of house prices in Bengaluru, but its accuracy could be further improved.

## 7. Future Work

- Incorporate more advanced feature engineering, such as using geographical coordinates for locations.
- Experiment with hyperparameter tuning on the Random Forest model to potentially boost performance further.
- Deploy the final model as a simple web application using FastAPI.
