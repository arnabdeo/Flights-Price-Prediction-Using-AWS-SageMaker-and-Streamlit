# Flight Price Prediction using AWS SageMaker and Streamlit

## Overview
This project aims to predict flight ticket prices using **XGBoost** as the machine learning model. The model is trained using **AWS SageMaker**, and the final application is deployed via **Streamlit**. The focus of this project is to leverage AWS services efficiently to minimize cloud costs while maintaining reasonable predictive performance.

## Project Workflow
1. **Data Collection & Preprocessing**
2. **Feature Engineering**
3. **Model Selection & Training (XGBoost on AWS SageMaker)**
4. **Hyperparameter Tuning**
5. **Model Evaluation**
6. **Model Deployment using Streamlit**

---

## 1. Data Collection & Preprocessing
- The dataset consists of flight details such as **airline, departure time, arrival time, duration, number of stops, and price**.
- Performed **data cleaning**, handling missing values, and removing anomalies.
- Categorical features like airline names and source/destination airports were **encoded using one-hot encoding**.
- Feature scaling and transformations applied where necessary.

## 2. Feature Engineering
- Extracted additional features such as:
  - **Day, Month, Year** from departure date.
  - **Time of Day (Morning, Afternoon, Evening, Night)**.
  - **Duration in hours** instead of raw text format.
  - **Binary encoding for categorical features**.

## 3. Model Selection & Training (XGBoost on AWS SageMaker)
- Used **AWS SageMaker Notebook Instance** for model development.
- Chose **XGBoost**, a powerful gradient boosting algorithm, for price prediction.
- Converted dataset into **DMatrix** format for optimized performance.
- Splitted data into **train, validation, and test sets**.

## 4. Hyperparameter Tuning
- Used **SageMaker Automatic Model Tuning** to optimize parameters.
- Focused on hyperparameters like:
  - `max_depth`
  - `learning_rate`
  - `n_estimators`
  - `min_child_weight`
- Prioritized **cost-efficient tuning** to avoid unnecessary cloud expenses.
- Achieved a balance between model performance and AWS resource utilization.

## 5. Model Evaluation
- Evaluated model performance using **RMSE, MAE, and R² scores**.
- Compared results with baseline models to validate effectiveness.
- Selected the best-performing model for deployment.

## 6. Model Deployment using Streamlit
- The trained model was **downloaded from SageMaker** and integrated into a **Streamlit web application**.
- Features of the app:
  - User inputs flight details (e.g., airline, departure, destination, duration, stops).
  - The model runs locally within the Streamlit app to make predictions.
  - Displays the predicted flight price.
- Streamlit hosted on **AWS EC2** to minimize cost.

---

## AWS Cost Optimization Strategies
- Used **Spot Instances** for training to reduce costs.
- Limited the number of hyperparameter tuning jobs to avoid excessive charges.
- Focused on local deployment via **Streamlit** to avoid unnecessary cloud inference costs.
- Used **AWS Free Tier** where possible.

---

## How to Run the Project
1. **Setup AWS Environment:**
   - Create an **S3 bucket** for data storage.
   - Launch an **AWS SageMaker Notebook Instance**.
   - Upload the dataset to S3.

2. **Train the Model:**
   - Use the provided Jupyter notebook to preprocess data and train XGBoost.
   - Save the trained model to **S3**.

3. **Download and Deploy the Model in Streamlit:**
   - Download the trained model from S3.
   - Load the model in a **Streamlit** application.
   - Install dependencies: `pip install -r requirements.txt`
   - Run: `streamlit run app.py`
   - Input flight details and get price predictions.

---

## Technologies Used
- **AWS Services:** SageMaker, EC2, S3
- **ML Framework:** XGBoost
- **Frontend:** Streamlit
- **Programming Language:** Python

---

## Future Improvements
- Enhance feature selection with **advanced NLP techniques** for text-based data.
- Implement **batch inference** instead of real-time to further reduce costs.
- Explore **serverless deployment options** to eliminate idle costs.

---

## Conclusion
This project demonstrates how to efficiently utilize **AWS SageMaker** for machine learning while keeping cloud expenses under control. By deploying the model via **Streamlit**, users can easily interact with predictions without needing deep technical knowledge.

Feel free to contribute or suggest improvements!


