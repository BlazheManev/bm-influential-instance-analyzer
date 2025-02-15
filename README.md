## Influential Analysis

## 📌 Overview
**Influential Analysis** is a Python library for identifying and analyzing **influential instances** in machine learning models. It helps assess model accuracy and fairness by detecting data points that significantly impact predictions. This is especially useful for bias detection and fairness auditing.

## 🔥 Features
- Identify **influential instances** that impact model fairness & accuracy
- Supports **classification models** (e.g., Decision Trees, Random Forests, etc.)
- Uses **Fairlearn** for fairness assessment
- Provides **visualization** of influential data points

## 📦 Installation
Install the package using:
```bash
pip install influential-analysis
```

## 🚀 Usage
### **1. Import the Library**
```python
!pip install influential-analysis==0.1.1
from influential_analysis.influential_analysis import InfluentialInstanceAnalyzer
```

### **2. Train Your Model**
```python
from sklearn.tree import DecisionTreeClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score
import pandas as pd

# Load Data
df = pd.read_csv("your_dataset.csv")
X = df.drop(columns=["target_column"])
y = df["target_column"]

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Train Model
model = DecisionTreeClassifier()
model.fit(X_train, y_train)
```

### **3. Analyze Influential Instances**
```python
sensitive_features = ["gender", "race"]  # Adjust based on dataset
analyzer = InfluentialInstanceAnalyzer(model, sensitive_features, deletion_percentage=10)

# Run analysis
analyzer.fit(X_train, y_train, X_test, y_test)
influential_instances, scores, acc_changes, fairness_changes = analyzer.run_analysis(showGraph=True)
```

### **4. Remove Influential Instances & Retrain**
```python
X_filtered = X.drop(index=influential_instances, errors='ignore')
y_filtered = y.drop(index=influential_instances, errors='ignore')

X_train_f, X_test_f, y_train_f, y_test_f = train_test_split(X_filtered, y_filtered, test_size=0.2, random_state=42)
model.fit(X_train_f, y_train_f)
```

## 📊 Visualization
The library supports **visualizing influential instances** using Seaborn:
```python
analyzer.run_analysis(showGraph=True)
```

## 🛠 Dependencies
- **NumPy**
- **Pandas**
- **Seaborn**
- **Matplotlib**
- **Scikit-learn**
- **Fairlearn**

## 🤝 Contributing
Contributions are welcome! Feel free to submit issues or pull requests on [GitHub](https://github.com/BlazheManev/bm-influential-instance-analyzer).

## 📧 Contact
Author: **Blazhe Manev**  
GitHub: [BlazheManev](https://github.com/BlazheManev)

