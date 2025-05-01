<h1>
  <span class="headline">AI Model Deployment</span>
  <span class="subhead">Hands-on Exercise + Best Practices Recap</span>
</h1>

## Hands-on Exercise: Deploying a Simple AI Model

In this exercise, you will deploy a basic AI model and interact with it through an API. The goal is to get hands-on experience with deploying models in a simple and reproducible way using tools available in your Docker-based environment.

### **Step 1: Train and Save a Model Using Scikit-learn**

We'll train a simple machine learning model using **scikit-learn** and save it for deployment.

```python
import pandas as pd
import numpy as np
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split
from sklearn.datasets import load_iris
from sklearn.metrics import accuracy_score
import joblib
import mlflow
import mlflow.sklearn

data = load_iris()
df = pd.DataFrame(data.data, columns=data.feature_names)
labels = data.target

X_train, X_test, y_train, y_test = train_test_split(df, labels, test_size=0.2, random_state=42)

with mlflow.start_run() as run:
    n_estimators = 100
    random_state = 42

    mlflow.log_param("n_estimators", n_estimators)
    mlflow.log_param("random_state", random_state)
    print(f"Logged parameters: n_estimators={n_estimators}, random_state={random_state}")

    model = RandomForestClassifier(n_estimators=n_estimators, random_state=random_state)
    model.fit(X_train, y_train)

    y_pred = model.predict(X_test)
    accuracy = accuracy_score(y_test, y_pred)

    mlflow.log_metric("accuracy", accuracy)
    print(f"Logged metric: accuracy={accuracy:.4f}")

    mlflow.sklearn.log_model(
        sk_model=model,
        artifact_path="iris-random-forest-model",
    )
    print("Model logged to MLflow Tracking Server under run_id:", run.info.run_id)

    local_save_path = "sklearn_iris_model_local"
    mlflow.sklearn.save_model(model, local_save_path)
    print(f"Model also saved locally at: {local_save_path}")

print("MLflow run completed.")

```

### **Step 2: Deploy the Model Using MLflow**

Open a new terminal and run this command.

```bash
sudo docker exec -it -w /app sa-course-labs mlflow models serve -m ./sklearn_iris_model_local --port 5001 --no-conda
```

This will launch a REST API that can be used to make predictions.

### **Step 3: Make a Prediction Request**

You can send a request to the deployed model using Python:

```python
import requests
import json
from sklearn.datasets import load_iris

data_loader = load_iris()

url = "http://127.0.0.1:5001/invocations"

data_payload = {
    "dataframe_split": {
        "columns": data_loader.feature_names,
        "data": [[5.1, 3.5, 1.4, 0.2]]
    }
}

try:
    response = requests.post(url, json=data_payload, headers={"Content-Type": "application/json"}, timeout=10)
    response.raise_for_status()
    print("Prediction Response:", response.json())
except requests.exceptions.RequestException as e:
    print(f"Error making prediction request: {e}")
except Exception as e:
    print(f"An unexpected error occurred: {e}")
```

### **Step 4: Stop the terminal opened on step 2 with Ctrl-C

---

## Best Practices Recap

### **Key Takeaways for AI Model Deployment**

- **Use Available Tools:** Leverage **scikit-learn** for training and **MLflow** for easy model deployment.
- **APIs for Model Interaction:** Exposing models via APIs allows seamless integration into applications.
- **Optimize Deployment:** Consider optimizing model size and response times when moving to production.
- **Security & Reliability:** Always consider access control and monitoring for deployed models.
- **Scalability Strategies:** When moving beyond local deployment, consider containerization (e.g., Docker) and cloud-based solutions.
-

