# End-to-End MLops Pipeline

**Repository:** `end-to-end-mlops-pipeline`  
**Project Overview:** This project demonstrates a **complete end-to-end ML workflow** using a real-world dataset, incorporating **DVC for data versioning**, **MLflow for experiment tracking**, and **FastAPI for model deployment**. The pipeline covers the **entire ML lifecycle**, from data collection and preprocessing to model training, tracking, and serving.

---

## **Table of Contents**
1. [Project Description](#project-description)
2. [Dataset](#dataset)
3. [Architecture](#architecture)
4. [Tools & Technologies](#tools--technologies)
5. [Setup Instructions](#setup-instructions)
6. [MLflow Experiments](#mlflow-experiments)
7. [API Deployment with FastAPI](#api-deployment-with-fastapi)
8. [Key Features & Resume Highlights](#key-features--resume-highlights)
9. [Future Work](#future-work)

---

## **Project Description**
This project demonstrates an **industry-grade ML pipeline**:
- Data versioning with **DVC** for reproducibility
- Experiment tracking with **MLflow** for metrics, parameters, and model artifacts
- Real-time **model serving** using **FastAPI**
- Clear separation of **data, experiments, and code**
- Fully **reproducible workflow** from Kaggle dataset to API deployment

---

## **Dataset**
**Diabetes Prediction Dataset (Pima Indians)** from Kaggle:  
- 768 samples, 8 features + target  
- Features include: `Pregnancies, Glucose, BloodPressure, SkinThickness, Insulin, BMI, DiabetesPedigreeFunction, Age`  
- Target: `Outcome` (0 = No Diabetes, 1 = Diabetes)  

📥 Kaggle Link: [Diabetes Dataset](https://www.kaggle.com/datasets/mathchi/diabetes-data-set)

---

## **Architecture**

```text
Kaggle Dataset
      │
      ▼
   DVC (Data Versioning)
      │
      ▼
Data Preprocessing
      │
      ▼
  ML Model Training
      │
      ▼
MLflow Experiment Tracking (parameters, metrics, models)
      │
      ▼
Model Saved & Logged
      │
      ▼
FastAPI Deployment (Prediction API)
      │
      ▼
Clients / Applications

| Layer               | Tool                               |
| ------------------- | ---------------------------------- |
| Data Versioning     | DVC                                |
| Experiment Tracking | MLflow                             |
| Model Training      | Scikit-learn (Logistic Regression) |
| Model Deployment    | FastAPI, Uvicorn                   |
| Notebook / Cloud    | Google Colab                       |
| Optional Tunneling  | Ngrok (requires account)           |

**Setup Instructions**

Clone the repository:

git clone https://github.com/<your-username>/end-to-end-mlops-pipeline.git
cd end-to-end-mlops-pipeline


**Install dependencies:**

pip install -r requirements.txt


**Dataset & DVC:**

dvc pull data/raw/diabetes.csv.dvc


Run the notebook end_to_end_ml_pipeline_dvc_mlflow_fastapi.ipynb in Colab.

**MLflow Experiments**

Models, metrics, and parameters are tracked using MLflow.

Example:

mlflow.log_param("model_type", "LogisticRegression")
mlflow.log_metric("accuracy", 0.78)
mlflow.sklearn.log_model(model, "model")


UI can be launched locally with:

mlflow ui --port 5000


In Colab, optional tunneling via ngrok (requires verified account).

API Deployment with FastAPI

Model can be served in real-time using FastAPI.

Example endpoint:
POST /predict
{
  "data": [2, 120, 70, 20, 79, 25.0, 0.5, 33]
}

**Returns prediction:**
{"prediction": 1}

Key Features & Resume Highlights

Full ML Lifecycle: Kaggle dataset → Data versioning → Training → Experiment tracking → Deployment

Enterprise-grade Tools: DVC, MLflow, FastAPI

Reproducibility: Model and data fully tracked and versioned

Interview-ready: Can explain architecture, CI/CD workflow, and production readiness

Future Work

Deploy API to cloud provider (AWS/GCP/Azure)

Add continuous integration & deployment (CI/CD) with GitHub Actions

Experiment with advanced models and hyperparameter tuning

Add unit tests for API endpoints 
