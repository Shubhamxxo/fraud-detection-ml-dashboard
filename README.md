# 🛡️ FraudSentinel AI — Credit Card Fraud Detection
### Real-Time Machine Learning Fraud Detection Dashboard

```
██████╗ ██████╗  █████╗ ██╗   ██╗██████╗ 
██╔════╝██╔══██╗██╔══██╗██║   ██║██╔══██╗
█████╗  ██████╔╝███████║██║   ██║██║  ██║
██╔══╝  ██╔══██╗██╔══██║██║   ██║██║  ██║
██║     ██║  ██║██║  ██║╚██████╔╝██████╔╝
╚═╝     ╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝ ╚═════╝ 
    SENTINEL AI - FRAUD DETECTION SYSTEM
```

---

## 📋 TABLE OF CONTENTS
1. [What This Project Does](#what-it-does)
2. [Tech Stack](#tech-stack)
3. [Project Structure](#project-structure)
4. [Step-by-Step Setup (Windows)](#setup-windows)
5. [Understanding the Dataset](#understanding-dataset)
6. [Understanding the ML Model](#understanding-ml)
7. [How the Dashboard Works](#dashboard)
8. [API Reference](#api)
9. [Troubleshooting](#troubleshooting)

---

## 🎯 WHAT THIS PROJECT DOES <a id="what-it-does"></a>

This project detects **fraudulent credit card transactions** using Machine Learning.

### The Core Problem:
- Credit card fraud costs billions of dollars every year
- Fraudulent transactions are **extremely rare** (only ~0.17% of all transactions)
- Normal models fail because they just predict "everything is legit" and get 99.83% accuracy!
- We need special techniques to catch that rare 0.17% fraud

### Our Solution:
| Component | What It Does |
|---|---|
| **Synthetic Dataset** | 50,000 realistic transactions with 30 features |
| **SMOTE Oversampling** | Creates artificial fraud samples to balance the dataset |
| **Random Forest** | 200 decision trees voting on each transaction |
| **XGBoost** | Gradient boosted trees for comparison |
| **Flask API** | REST API serving predictions in real-time |
| **Cyberpunk Dashboard** | Live transaction feed, charts, risk analysis |

---

## 🛠️ TECH STACK <a id="tech-stack"></a>

```
Python 3.10+
├── scikit-learn     → Machine Learning models
├── imbalanced-learn → SMOTE oversampling
├── XGBoost          → Gradient boosting
├── pandas/numpy     → Data processing
├── Flask            → Web server / REST API
└── Chart.js         → Dashboard charts (CDN)
```

---

## 📁 PROJECT STRUCTURE <a id="project-structure"></a>

```
credit_fraud_detection/
│
├── 📄 app.py                        ← Flask web server (RUN THIS LAST)
├── 📄 requirements.txt              ← Python dependencies
├── 📄 README.md                     ← You're reading this!
│
├── 📂 dataset/
│   ├── generate_dataset.py          ← Creates credit_card_data.csv
│   └── credit_card_data.csv         ← Generated after Step 4
│
├── 📂 model/
│   ├── train_model.py               ← Trains and saves the ML model
│   ├── fraud_model.pkl              ← Saved model (after training)
│   ├── scaler.pkl                   ← Feature scaler (after training)
│   ├── feature_cols.pkl             ← Feature list (after training)
│   ├── feature_importance.csv       ← Feature ranks (after training)
│   └── model_results.csv            ← Model comparison (after training)
│
└── 📂 templates/
    └── index.html                   ← The dashboard UI
```

---

## 🖥️ STEP-BY-STEP SETUP (WINDOWS) <a id="setup-windows"></a>

### ─────────────────────────────────────────
### STEP 1: Check Python is Installed
### ─────────────────────────────────────────

Open **Command Prompt** (search "cmd" in Start menu) and type:
```cmd
python --version
```
You should see `Python 3.10.x` or higher.

❌ If you get an error → Download Python from: https://python.org/downloads
   ✅ During install, CHECK the box **"Add Python to PATH"**

---

### ─────────────────────────────────────────
### STEP 2: Navigate to Project Folder
### ─────────────────────────────────────────

In Command Prompt, navigate to where you saved this project:
```cmd
cd C:\Users\YourName\credit_fraud_detection
```
Replace `YourName` with your actual Windows username.

**Tip:** You can also right-click inside the folder → "Open in Terminal"

---

### ─────────────────────────────────────────
### STEP 3: Create a Virtual Environment
### ─────────────────────────────────────────

A virtual environment keeps this project's packages separate from others.

```cmd
python -m venv fraud_env
```

**Activate it:**
```cmd
fraud_env\Scripts\activate
```

You'll see `(fraud_env)` appear at the start of your prompt. ✅

---

### ─────────────────────────────────────────
### STEP 4: Install Required Packages
### ─────────────────────────────────────────

```cmd
pip install -r requirements.txt
```

This installs: scikit-learn, XGBoost, Flask, pandas, numpy, imbalanced-learn

⏳ This may take 2-5 minutes. Coffee time ☕

---

### ─────────────────────────────────────────
### STEP 5: Generate the Dataset
### ─────────────────────────────────────────

```cmd
python dataset\generate_dataset.py
```

**What happens:**
- Creates 50,000 synthetic credit card transactions
- Saves as `dataset/credit_card_data.csv`
- Shows statistics about the generated data

✅ Expected output:
```
✅ DATASET GENERATED SUCCESSFULLY!
📐 Shape: 50,000 rows × 31 columns
Legit (0): 49,915 transactions (99.830%)
Fraud (1):     85 transactions (0.170%)
```

---

### ─────────────────────────────────────────
### STEP 6: Train the Machine Learning Model
### ─────────────────────────────────────────

```cmd
python model\train_model.py
```

**What happens:**
1. Loads the dataset
2. Scales Amount and Time features
3. Splits into 80% training, 20% testing
4. Applies SMOTE to balance fraud/legit ratio
5. Trains Random Forest, Logistic Regression, XGBoost
6. Picks the best model by AUC-ROC score
7. Saves model files to `model/` folder

⏳ This takes 2-5 minutes (training 200+ trees).

✅ Expected output:
```
🏆 Best Model: Random Forest
AUC-ROC: 0.97+
F1-Score: 0.85+
Fraud Caught: XX/XX (95%+)
```

---

### ─────────────────────────────────────────
### STEP 7: Launch the Dashboard
### ─────────────────────────────────────────

```cmd
python app.py
```

You'll see:
```
🚀 CREDIT CARD FRAUD DETECTION WEB APP
✅ Model loaded and ready!
🌐 Open: http://127.0.0.1:5000
```

**Open your browser and go to:**
```
http://127.0.0.1:5000
```

🎉 **The FraudSentinel dashboard will appear!**

---

### ─────────────────────────────────────────
### STEP 8: Use the Dashboard
### ─────────────────────────────────────────

**Live Transaction Feed:**
- Click **▶ SIMULATE** → Starts auto-generating transactions every 1.8 seconds
- Red rows = fraud detected
- Click **LOAD BATCH** → Adds 10 transactions at once

**Analyze a Transaction:**
- Click **RANDOM FILL** to auto-populate
- Or enter your own Amount and V1-V4 values
- Click **⚡ ANALYZE FRAUD RISK**
- Result shows fraud probability + risk level

**Dashboard Sections:**
- 📊 KPI Cards → Dataset overview at a glance
- 💳 Amount Distribution → Fraud vs legit spending patterns
- 🎯 Class Distribution → Donut chart of fraud ratio
- 📐 Confusion Matrix → How well the model performs
- ⚡ Live Feed → Real-time transaction stream
- 📊 Feature Importance → Which V-features matter most
- 🤖 Model Comparison → Random Forest vs XGBoost vs Logistic Regression

---

## 📊 UNDERSTANDING THE DATASET <a id="understanding-dataset"></a>

### Feature Descriptions:

| Column | Type | Description |
|--------|------|-------------|
| `Time` | float | Seconds elapsed since first transaction in dataset |
| `V1`–`V28` | float | PCA-transformed anonymized card features |
| `Amount` | float | Transaction amount in USD |
| `Class` | int | **Target**: 0=Legitimate, 1=Fraud |

### Why V1-V28?
Real credit card datasets (like from Kaggle) use PCA to anonymize sensitive customer data. V1-V28 represent 28 principal components of the original features (card number, location, merchant type, etc.).

### Class Imbalance:
```
Normal:  49,915  (99.83%)  ████████████████████████████████████████
Fraud:       85   (0.17%)  ▌
```
This is the core challenge! A naive model just predicts "legit" every time.

---

## 🤖 UNDERSTANDING THE ML MODEL <a id="understanding-ml"></a>

### Step 1: Feature Scaling
`Amount` and `Time` have very different ranges than V1-V28.
`StandardScaler` normalizes them to mean=0, std=1.

### Step 2: SMOTE (Synthetic Minority Oversampling)
```
Before SMOTE:  Fraud=85,    Legit=39,932
After  SMOTE:  Fraud=39,932, Legit=39,932  ← Balanced!
```
SMOTE creates new fraud samples by interpolating between real fraud points.

### Step 3: Random Forest
- Builds 200 decision trees, each trained on a random subset
- Each tree votes: "fraud" or "legit"
- Majority vote = final prediction
- Provides probability score (0-100%)

### Step 4: Evaluation Metrics
| Metric | Meaning |
|--------|---------|
| **AUC-ROC** | Area under ROC curve. 1.0 = perfect, 0.5 = random |
| **Precision** | Of all flagged fraud, % that are actually fraud |
| **Recall** | Of all actual fraud, % that were caught |
| **F1-Score** | Harmonic mean of precision and recall |

### Why AUC-ROC and not Accuracy?
Accuracy is misleading here! If you predict "legit" for everything:
- Accuracy = 99.83% ← looks great!
- But Recall = 0% ← catches NO fraud at all! ❌

AUC-ROC properly measures fraud detection ability.

---

## 🌐 API REFERENCE <a id="api"></a>

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/` | GET | Dashboard HTML |
| `/api/stats` | GET | Dataset & model statistics |
| `/api/predict` | POST | Predict single transaction |
| `/api/simulate` | GET | Generate fake transactions |
| `/api/features` | GET | Feature importance |
| `/api/amount_distribution` | GET | Amount histogram data |

### Example: Predict via curl
```cmd
curl -X POST http://127.0.0.1:5000/api/predict ^
  -H "Content-Type: application/json" ^
  -d "{\"Amount\": 150.00, \"V1\": -3.5, \"V2\": 2.1, \"V3\": -4.0, \"V4\": 3.2, \"Time\": 50000}"
```

Response:
```json
{
  "prediction": 1,
  "fraud_prob": 87.3,
  "legit_prob": 12.7,
  "risk_level": "HIGH",
  "is_fraud": true,
  "timestamp": "2024-01-15 14:23:11"
}
```

---

## 🔧 TROUBLESHOOTING <a id="troubleshooting"></a>

### ❌ "ModuleNotFoundError: No module named 'flask'"
**Fix:** Make sure your virtual environment is activated:
```cmd
fraud_env\Scripts\activate
pip install -r requirements.txt
```

### ❌ "FileNotFoundError: credit_card_data.csv not found"
**Fix:** Run dataset generation first:
```cmd
python dataset\generate_dataset.py
```

### ❌ "FileNotFoundError: fraud_model.pkl not found"
**Fix:** Train the model first:
```cmd
python model\train_model.py
```

### ❌ Browser shows "Cannot connect" or blank page
**Fix:** Make sure Flask is running:
```cmd
python app.py
```
Then visit: http://127.0.0.1:5000

### ❌ XGBoost installation fails
**Fix:** Skip XGBoost by modifying requirements.txt (remove xgboost line).
The system will use Random Forest as the best model.

### ❌ Charts not loading in dashboard
**Fix:** You need an internet connection (Chart.js loads from CDN).
If offline, download Chart.js and change the script src to a local path.

---

## 📈 EXPECTED PERFORMANCE

| Model | AUC-ROC | F1-Score |
|-------|---------|----------|
| Random Forest | ~0.96-0.99 | ~0.80-0.90 |
| XGBoost | ~0.95-0.98 | ~0.78-0.88 |
| Logistic Reg | ~0.87-0.93 | ~0.65-0.78 |

---

## 🔬 EXTENDING THE PROJECT

Ideas to take it further:
1. **Real Dataset**: Download the Kaggle Credit Card Fraud dataset (creditcardfraud.zip)
2. **Deep Learning**: Add a Neural Network (TensorFlow/Keras)
3. **Real-Time DB**: Connect PostgreSQL to store all analyzed transactions
4. **Email Alerts**: Send email when fraud is detected (Flask-Mail)
5. **Docker**: Package the app for deployment
6. **Cloud Deploy**: Host on AWS/GCP/Azure

---
