### 🩺 Interactive Diabetes Prediction System (PIMA Dataset)

## Overview
This project delivers a complete, end-to-end solution for real-time diabetes risk assessment. It utilizes a Logistic Regression machine learning model trained on the Pima Indians Diabetes Dataset and integrates it into a user-friendly, client-side HTML/JavaScript dashboard.
The key feature is a "What-If" Analysis graph that updates instantly, showing the user how changes to a single health metric (like Glucose or BMI) affect their final probability score.

## 📁 Project Structure
The project has two primary files:
- `model_training.py:` The Python script used for all data science tasks (loading, cleaning, scaling, training, and extracting parameters).
- `index.html:` The static web application containing all HTML, CSS (Tailwind), and JavaScript logic for the interactive prediction and graphing.

## 🚀 Getting Started
To run this project, you need to execute two simple steps: one for the model and one for the web interface.
# Step 1: Train the Model and Extract Parameters
1. **Dependencies:** Ensure you have Python, `pandas`, and `scikit-learn` installed (`pip install pandas scikit-learn numpy`).
2. **Run the script:** Execute the Python training file.
```
python model_training.py
```
3. **Capture Output:** The script will print the final accuracy and, most importantly, the four sets of parameters required for the web app: `Scaler Means`, `Scaler Scales`, `Model Intercept`, and `Model Coefficients`.

# Step 2: Run the Web Application
1. **Copy Parameters:** Open your `index.html` file and navigate to the `<script>` section at the bottom.
2. **Paste Values:** Replace the placeholder arrays for `SCALER_MEANS`, `SCALER_SCALES`, `MODEL_INTERCEPT`, and `MODEL_COEFS` with the precise values printed by `model_training.py`.
3. **Launch:** Open the saved `index.html` file directly in any modern web browser (Chrome, Firefox, Edge). No server is required.

## 📊 Technical Deep Dive
# Data Preprocessing
- **Dataset:** Pima Indians Diabetes Dataset (768 records, 8 features).
- **Missing Value Handling:** Biologically impossible '0' values in features like `Glucose`, `BMI`, `BloodPressur`, `SkinThickness`, and `Insulin` were identified as missing data and were replaced using __Median Imputation__ to minimize the impact of outliers.
- **Scaling:** All 8 features were scaled using `StandardScaler` to ensure equal weighting during model training.

# Model Performance
| Metric | Algorithm | Value |
|---|---|---|
| **Model Type** | Logistic Regression | Classification |
| **Test Accuracy** |  | 75.32% |

# Key Features of the Web Dashboard
| Feature | Technology | Description |
|---|---|---|
| **Real-time Prediction** | Pure JavaScript | The web app re-implements the model's math (including scaling and the Sigmoid function) to give instant risk scores as the user types. |
| **"What-If" Analysis** | Chart.js & Annotation Plugin | A line graph plots the predicted probability across the entire range of a single selected feature (e.g., Glucose), holding all other inputs constant. |
| **Current Value Marker** | Annotation Plugin | A red dashed line and point mark the patient's current input value on the "What-If" curve for easy context and interpretation. |
| Aesthetics | Tailwind CSS | Ensures a responsive, clean, and mobile-friendly interface. |

## 🛠️ Technologies Used
- **Python:** Data cleaning, training, parameter extraction.
- **Libraries:** pandas, scikit-learn, numpy.
- **Frontend:** HTML5, CSS (Tailwind CSS), JavaScript.
- **Visualization**: Chart.js, chartjs-plugin-annotation.
