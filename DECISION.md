# Engineering Decisions & Project Post-Mortem

## Task: Placement Readiness Predictor

### 1. Data Preprocessing & Pipeline
* **Handling Missing Values:** Cleaned the dataset using `dropna()` to remove incomplete rows before training.
* **Categorical Encoding:** Applied `pd.get_dummies()` to convert text features into binary dummy variables (0s and 1s) so Scikit-Learn models could process them.
* **Train/Test Split:** Used an 80/20 train-test split (`test_size=0.2`, `random_state=42`) to evaluate model generalization on unseen data.

### 2. Model Evaluation & Comparison
Compared two binary classification models using Precision, Recall, and Accuracy metrics:

| Model | Accuracy |
| :--- | :--- |
| Logistic Regression | [PASTE CELL 4 ACCURACY HERE, e.g., 82%] |
| Random Forest Classifier | [PASTE CELL 5 ACCURACY HERE, e.g., 87%] |

**Key Finding:** The Random Forest model performed [better / similarly] because decision-tree ensemble methods capture non-linear feature interactions better than linear models.

### 3. Debugging & Challenges
* **KeyError on Target Column:** Encountered a `KeyError` during `df.drop()` because the target column name differed from the initial assumption[cite: 3]. Fixed by inspecting `df.columns` and updating the target variable name to match the dataset[cite: 3].
* **String Input Error:** Passing raw categorical text into model fitting threw an error, which was resolved by applying one-hot encoding prior to train-test splitting.

### 4. Future Improvements
* Build an interactive UI using **Streamlit** to allow live user inputs for instant placement prediction.
* Apply hyperparameter tuning using `GridSearchCV` to optimize the Random Forest tree depth and estimators.