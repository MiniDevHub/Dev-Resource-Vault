<div align="center">

# 🤖 Machine Learning Frameworks - Complete Guide

![ML](https://img.shields.io/badge/Machine_Learning-Frameworks-red?style=for-the-badge&logo=tensorflow)
![Python](https://img.shields.io/badge/Python-ML-blue?style=for-the-badge&logo=python)
![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=for-the-badge)

### _From classical ML to deep learning - master them all_ 🚀

**Build intelligent systems with the right tools** ✨

</div>

---

## 📚 Table of Contents

- [🎯 Framework Overview](#-framework-overview)
- [📊 Scikit-learn](#-scikit-learn)
- [🧠 TensorFlow & Keras](#-tensorflow--keras)
- [🔥 PyTorch](#-pytorch)
- [⚡ Gradient Boosting](#-gradient-boosting)
- [🌟 Other Frameworks](#-other-frameworks)
- [📊 Framework Comparison](#-framework-comparison)
- [🚀 Model Deployment](#-model-deployment)
- [💡 Best Practices](#-best-practices)
- [🔧 Real-World Projects](#-real-world-projects)

---

<div align="center">

## 🎯 Framework Overview

</div>

### Understanding ML Frameworks 📖

```bash
# ═══════════════════════════════════════════
# MACHINE LEARNING FRAMEWORK LANDSCAPE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHAT ARE ML FRAMEWORKS?                  ║
╚════════════════════════════════════════════════════════════╝

Machine Learning Frameworks: Tools and libraries for building ML models
─────────────────────────────────────────────────────────────
• Pre-built algorithms and tools
• Handle complex mathematics
• Optimize performance
• Simplify model development
• Provide deployment capabilities

Evolution:
─────────────────────────────────────────────────────────────
2007: Scikit-learn    → Classical ML
2011: Torch           → Deep Learning (Lua)
2015: TensorFlow      → Google's DL framework
2016: Keras           → High-level DL API
2016: PyTorch         → Facebook's DL framework
2016: XGBoost         → Gradient boosting
2017: LightGBM        → Fast gradient boosting
2017: CatBoost        → Categorical features
2018: FastAI          → Simplified deep learning
2018: JAX             → High-performance ML

╔════════════════════════════════════════════════════════════╗
║                   FRAMEWORK CATEGORIES                     ║
╚════════════════════════════════════════════════════════════╝

Classical ML:
─────────────────────────────────────────────────────────────
• Scikit-learn        ⭐ Industry standard
• Statsmodels         Statistical models
• MLJAR               AutoML

Deep Learning:
─────────────────────────────────────────────────────────────
• TensorFlow/Keras    ⭐ Production-ready
• PyTorch             ⭐ Research-friendly
• FastAI              Beginner-friendly
• JAX                 High-performance

Gradient Boosting:
─────────────────────────────────────────────────────────────
• XGBoost             ⭐ Most popular
• LightGBM            ⭐ Fastest
• CatBoost            ⭐ Handles categories

Specialized:
─────────────────────────────────────────────────────────────
• Hugging Face        NLP/Transformers
• OpenCV              Computer Vision
• Surprise            Recommendation Systems
• PySpark MLlib       Big Data ML

╔════════════════════════════════════════════════════════════╗
║                   FRAMEWORK COMPARISON                     ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Framework        | Type              | Best For                        | Learning Curve | Production   | Community    |
| ---------------- | ----------------- | ------------------------------- | -------------- | ------------ | ------------ |
| **Scikit-learn** | Classical ML      | Tabular data, traditional ML    | ⭐ Easy        | ✅ Good      | ⭐⭐⭐ Huge  |
| **TensorFlow**   | Deep Learning     | Production, mobile, large scale | ⭐⭐⭐ Hard    | ✅ Excellent | ⭐⭐⭐ Huge  |
| **Keras**        | Deep Learning     | Prototyping, beginners          | ⭐ Easy        | ✅ Good      | ⭐⭐⭐ Large |
| **PyTorch**      | Deep Learning     | Research, flexibility           | ⭐⭐ Moderate  | ✅ Good      | ⭐⭐⭐ Huge  |
| **XGBoost**      | Gradient Boosting | Structured data, competitions   | ⭐⭐ Moderate  | ✅ Excellent | ⭐⭐⭐ Large |
| **LightGBM**     | Gradient Boosting | Large datasets, speed           | ⭐⭐ Moderate  | ✅ Excellent | ⭐⭐ Medium  |
| **CatBoost**     | Gradient Boosting | Categorical features            | ⭐⭐ Moderate  | ✅ Good      | ⭐⭐ Medium  |
| **FastAI**       | Deep Learning     | Quick prototyping               | ⭐ Easy        | ⚠️ Fair      | ⭐⭐ Growing |

</div>

```bash
╔════════════════════════════════════════════════════════════╗
║                   CHOOSING A FRAMEWORK                     ║
╚════════════════════════════════════════════════════════════╝

Decision Tree:
─────────────────────────────────────────────────────────────

What type of data?
├─ Tabular/Structured
│  ├─ Small/Medium (<100K rows)
│  │  └─ Scikit-learn ✅
│  ├─ Large (>100K rows)
│  │  └─ XGBoost / LightGBM ✅
│  └─ Many categorical features
│     └─ CatBoost ✅
│
├─ Images
│  ├─ Quick prototyping
│  │  └─ FastAI ✅
│  ├─ Custom architectures
│  │  └─ PyTorch ✅
│  └─ Production deployment
│     └─ TensorFlow ✅
│
├─ Text
│  ├─ Modern NLP (Transformers)
│  │  └─ Hugging Face ✅
│  ├─ Classical NLP
│  │  └─ Scikit-learn ✅
│  └─ Custom models
│     └─ PyTorch ✅
│
└─ Time Series
   ├─ Traditional forecasting
   │  └─ Statsmodels ✅
   ├─ Complex patterns
   │  └─ TensorFlow / PyTorch ✅
   └─ Tabular time series
      └─ XGBoost / LightGBM ✅

Use Case Recommendations:
─────────────────────────────────────────────────────────────
✅ Prototyping: Scikit-learn, Keras, FastAI
✅ Research: PyTorch, JAX
✅ Production: TensorFlow, XGBoost, Scikit-learn
✅ Kaggle/Competitions: XGBoost, LightGBM, CatBoost
✅ Edge devices: TensorFlow Lite, ONNX
✅ Big Data: PySpark MLlib, Dask-ML

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 📊 Scikit-learn

</div>

### The Swiss Army Knife of Machine Learning 🔧

```python
# ═══════════════════════════════════════════
# SCIKIT-LEARN FUNDAMENTALS
# ═══════════════════════════════════════════

"""
Scikit-learn: Most popular Python ML library
- Consistent API across algorithms
- Extensive documentation
- Production-ready
- Integrates with NumPy/Pandas
- 15+ years of development
"""

# Installation
# pip install scikit-learn

import numpy as np
import pandas as pd
from sklearn import datasets
import matplotlib.pyplot as plt

# ═══════════════════════════════════════════
# SUPERVISED LEARNING
# ═══════════════════════════════════════════

# ─────────────────────────────────────────────
# 1. CLASSIFICATION
# ─────────────────────────────────────────────

from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier
from sklearn.svm import SVC
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import (accuracy_score, classification_report,
                             confusion_matrix, roc_auc_score, roc_curve)

# Load dataset
from sklearn.datasets import load_breast_cancer
data = load_breast_cancer()
X, y = data.data, data.target

print(f"Dataset: {data.DESCR[:200]}...")
print(f"Features: {data.feature_names[:5]}...")
print(f"Shape: {X.shape}")
print(f"Classes: {data.target_names}")

# Split data
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42, stratify=y
)

# Scale features
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# Train multiple classifiers
classifiers = {
    'Logistic Regression': LogisticRegression(max_iter=10000),
    'Decision Tree': DecisionTreeClassifier(random_state=42),
    'Random Forest': RandomForestClassifier(n_estimators=100, random_state=42),
    'SVM': SVC(probability=True, random_state=42),
    'KNN': KNeighborsClassifier(n_neighbors=5)
}

results = {}
for name, clf in classifiers.items():
    # Train
    clf.fit(X_train_scaled, y_train)

    # Predict
    y_pred = clf.predict(X_test_scaled)
    y_pred_proba = clf.predict_proba(X_test_scaled)[:, 1] if hasattr(clf, 'predict_proba') else None

    # Evaluate
    accuracy = accuracy_score(y_test, y_pred)

    results[name] = {
        'model': clf,
        'accuracy': accuracy,
        'predictions': y_pred
    }

    print(f"\n{name}:")
    print(f"Accuracy: {accuracy:.4f}")

    if y_pred_proba is not None:
        auc = roc_auc_score(y_test, y_pred_proba)
        print(f"AUC-ROC: {auc:.4f}")

# Best model
best_model_name = max(results, key=lambda x: results[x]['accuracy'])
best_model = results[best_model_name]['model']
print(f"\n🏆 Best Model: {best_model_name}")

# Detailed evaluation
print("\nClassification Report:")
print(classification_report(y_test, results[best_model_name]['predictions'],
                          target_names=data.target_names))

# Confusion Matrix
cm = confusion_matrix(y_test, results[best_model_name]['predictions'])
print("\nConfusion Matrix:")
print(cm)

# ─────────────────────────────────────────────
# 2. REGRESSION
# ─────────────────────────────────────────────

from sklearn.linear_model import LinearRegression, Ridge, Lasso
from sklearn.tree import DecisionTreeRegressor
from sklearn.ensemble import RandomForestRegressor, GradientBoostingRegressor
from sklearn.metrics import mean_squared_error, r2_score, mean_absolute_error

# Load dataset
from sklearn.datasets import load_diabetes
diabetes = load_diabetes()
X, y = diabetes.data, diabetes.target

# Split data
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

# Train regressors
regressors = {
    'Linear Regression': LinearRegression(),
    'Ridge': Ridge(alpha=1.0),
    'Lasso': Lasso(alpha=1.0),
    'Decision Tree': DecisionTreeRegressor(random_state=42),
    'Random Forest': RandomForestRegressor(n_estimators=100, random_state=42),
    'Gradient Boosting': GradientBoostingRegressor(n_estimators=100, random_state=42)
}

print("\n" + "="*60)
print("REGRESSION MODELS")
print("="*60)

for name, reg in regressors.items():
    # Train
    reg.fit(X_train, y_train)

    # Predict
    y_pred = reg.predict(X_test)

    # Evaluate
    mse = mean_squared_error(y_test, y_pred)
    rmse = np.sqrt(mse)
    mae = mean_absolute_error(y_test, y_pred)
    r2 = r2_score(y_test, y_pred)

    print(f"\n{name}:")
    print(f"  RMSE: {rmse:.2f}")
    print(f"  MAE:  {mae:.2f}")
    print(f"  R²:   {r2:.4f}")

# ═══════════════════════════════════════════
# UNSUPERVISED LEARNING
# ═══════════════════════════════════════════

# ─────────────────────────────────────────────
# 1. CLUSTERING
# ─────────────────────────────────────────────

from sklearn.cluster import KMeans, DBSCAN, AgglomerativeClustering
from sklearn.metrics import silhouette_score, davies_bouldin_score

# Generate sample data
from sklearn.datasets import make_blobs
X, y_true = make_blobs(n_samples=300, centers=4,
                       cluster_std=0.60, random_state=42)

# K-Means
kmeans = KMeans(n_clusters=4, random_state=42)
y_kmeans = kmeans.fit_predict(X)

print("\n" + "="*60)
print("CLUSTERING")
print("="*60)
print(f"\nK-Means:")
print(f"  Inertia: {kmeans.inertia_:.2f}")
print(f"  Silhouette Score: {silhouette_score(X, y_kmeans):.4f}")

# DBSCAN
dbscan = DBSCAN(eps=0.5, min_samples=5)
y_dbscan = dbscan.fit_predict(X)
print(f"\nDBSCAN:")
print(f"  Number of clusters: {len(set(y_dbscan)) - (1 if -1 in y_dbscan else 0)}")
print(f"  Number of noise points: {list(y_dbscan).count(-1)}")

# Hierarchical Clustering
hierarchical = AgglomerativeClustering(n_clusters=4)
y_hierarchical = hierarchical.fit_predict(X)
print(f"\nHierarchical Clustering:")
print(f"  Silhouette Score: {silhouette_score(X, y_hierarchical):.4f}")

# ─────────────────────────────────────────────
# 2. DIMENSIONALITY REDUCTION
# ─────────────────────────────────────────────

from sklearn.decomposition import PCA, TruncatedSVD
from sklearn.manifold import TSNE

# Load high-dimensional data
digits = datasets.load_digits()
X = digits.data

print("\n" + "="*60)
print("DIMENSIONALITY REDUCTION")
print("="*60)
print(f"Original dimensions: {X.shape}")

# PCA
pca = PCA(n_components=2)
X_pca = pca.fit_transform(X)
print(f"\nPCA:")
print(f"  Reduced dimensions: {X_pca.shape}")
print(f"  Explained variance: {pca.explained_variance_ratio_.sum():.4f}")

# t-SNE
tsne = TSNE(n_components=2, random_state=42)
X_tsne = tsne.fit_transform(X)
print(f"\nt-SNE:")
print(f"  Reduced dimensions: {X_tsne.shape}")

# ═══════════════════════════════════════════
# MODEL SELECTION & VALIDATION
# ═══════════════════════════════════════════

from sklearn.model_selection import (cross_val_score, GridSearchCV,
                                    RandomizedSearchCV, StratifiedKFold)

# Load dataset
X, y = load_breast_cancer(return_X_y=True)
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

# ─────────────────────────────────────────────
# Cross-Validation
# ─────────────────────────────────────────────

model = RandomForestClassifier(random_state=42)

# Simple cross-validation
cv_scores = cross_val_score(model, X_train, y_train, cv=5)
print("\n" + "="*60)
print("CROSS-VALIDATION")
print("="*60)
print(f"CV Scores: {cv_scores}")
print(f"Mean: {cv_scores.mean():.4f} (+/- {cv_scores.std():.4f})")

# Stratified K-Fold
skf = StratifiedKFold(n_splits=5, shuffle=True, random_state=42)
cv_scores_stratified = cross_val_score(model, X_train, y_train, cv=skf)
print(f"\nStratified CV Scores: {cv_scores_stratified}")
print(f"Mean: {cv_scores_stratified.mean():.4f}")

# ─────────────────────────────────────────────
# Hyperparameter Tuning - Grid Search
# ─────────────────────────────────────────────

param_grid = {
    'n_estimators': [50, 100, 200],
    'max_depth': [5, 10, 15, None],
    'min_samples_split': [2, 5, 10],
    'min_samples_leaf': [1, 2, 4]
}

grid_search = GridSearchCV(
    RandomForestClassifier(random_state=42),
    param_grid,
    cv=5,
    scoring='accuracy',
    n_jobs=-1,
    verbose=1
)

print("\n" + "="*60)
print("GRID SEARCH")
print("="*60)
grid_search.fit(X_train, y_train)

print(f"\nBest parameters: {grid_search.best_params_}")
print(f"Best CV score: {grid_search.best_score_:.4f}")
print(f"Test score: {grid_search.score(X_test, y_test):.4f}")

# ─────────────────────────────────────────────
# Hyperparameter Tuning - Random Search
# ─────────────────────────────────────────────

from scipy.stats import randint

param_distributions = {
    'n_estimators': randint(50, 500),
    'max_depth': [5, 10, 15, 20, None],
    'min_samples_split': randint(2, 20),
    'min_samples_leaf': randint(1, 10)
}

random_search = RandomizedSearchCV(
    RandomForestClassifier(random_state=42),
    param_distributions,
    n_iter=20,
    cv=5,
    scoring='accuracy',
    n_jobs=-1,
    random_state=42
)

print("\n" + "="*60)
print("RANDOM SEARCH")
print("="*60)
random_search.fit(X_train, y_train)

print(f"\nBest parameters: {random_search.best_params_}")
print(f"Best CV score: {random_search.best_score_:.4f}")

# ═══════════════════════════════════════════
# PIPELINES
# ═══════════════════════════════════════════

from sklearn.pipeline import Pipeline, make_pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.feature_selection import SelectKBest, f_classif

# Create pipeline
pipeline = Pipeline([
    ('scaler', StandardScaler()),
    ('feature_selection', SelectKBest(f_classif, k=10)),
    ('classifier', RandomForestClassifier(random_state=42))
])

# Train pipeline
pipeline.fit(X_train, y_train)

# Predict
y_pred = pipeline.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)

print("\n" + "="*60)
print("PIPELINE")
print("="*60)
print(f"Pipeline accuracy: {accuracy:.4f}")

# Pipeline with GridSearch
param_grid = {
    'feature_selection__k': [5, 10, 15, 20],
    'classifier__n_estimators': [50, 100, 200],
    'classifier__max_depth': [5, 10, None]
}

grid_pipeline = GridSearchCV(pipeline, param_grid, cv=5, n_jobs=-1)
grid_pipeline.fit(X_train, y_train)

print(f"\nBest pipeline parameters: {grid_pipeline.best_params_}")
print(f"Best score: {grid_pipeline.best_score_:.4f}")

# ═══════════════════════════════════════════
# FEATURE ENGINEERING
# ═══════════════════════════════════════════

from sklearn.preprocessing import (StandardScaler, MinMaxScaler, RobustScaler,
                                   LabelEncoder, OneHotEncoder, PolynomialFeatures)
from sklearn.impute import SimpleImputer

# Sample data with missing values and categories
df = pd.DataFrame({
    'age': [25, 30, None, 40, 35],
    'income': [50000, 60000, 55000, None, 70000],
    'category': ['A', 'B', 'A', 'C', 'B'],
    'target': [0, 1, 0, 1, 1]
})

print("\n" + "="*60)
print("FEATURE ENGINEERING")
print("="*60)
print("\nOriginal data:")
print(df)

# Handle missing values
imputer = SimpleImputer(strategy='mean')
df[['age', 'income']] = imputer.fit_transform(df[['age', 'income']])

print("\nAfter imputation:")
print(df)

# Encode categorical variables
label_encoder = LabelEncoder()
df['category_encoded'] = label_encoder.fit_transform(df['category'])

# One-hot encoding
onehot = pd.get_dummies(df['category'], prefix='cat')
df = pd.concat([df, onehot], axis=1)

print("\nAfter encoding:")
print(df.head())

# Create polynomial features
X = df[['age', 'income']].values
poly = PolynomialFeatures(degree=2, include_bias=False)
X_poly = poly.fit_transform(X)

print(f"\nOriginal features: {X.shape}")
print(f"Polynomial features: {X_poly.shape}")
print(f"Feature names: {poly.get_feature_names_out(['age', 'income'])}")

# ═══════════════════════════════════════════
# MODEL PERSISTENCE
# ═══════════════════════════════════════════

import joblib
import pickle

# Train a model
model = RandomForestClassifier(n_estimators=100, random_state=42)
model.fit(X_train, y_train)

# Save with joblib (recommended)
joblib.dump(model, 'model.pkl')

# Load model
loaded_model = joblib.load('model.pkl')

# Verify
print("\n" + "="*60)
print("MODEL PERSISTENCE")
print("="*60)
print(f"Original model score: {model.score(X_test, y_test):.4f}")
print(f"Loaded model score: {loaded_model.score(X_test, y_test):.4f}")

# Save with pickle
with open('model_pickle.pkl', 'wb') as f:
    pickle.dump(model, f)

# Load with pickle
with open('model_pickle.pkl', 'rb') as f:
    model_pickle = pickle.load(f)

print(f"Pickle model score: {model_pickle.score(X_test, y_test):.4f}")

print("\n✅ Scikit-learn complete!")
```

---

<div align="center">

## 🧠 TensorFlow & Keras

</div>

### Deep Learning for Production 🏭

```python
# ═══════════════════════════════════════════
# TENSORFLOW & KERAS FUNDAMENTALS
# ═══════════════════════════════════════════

"""
TensorFlow: Google's deep learning framework
Keras: High-level API for TensorFlow
- Production-ready
- Mobile and web deployment
- Distributed training
- TensorFlow Serving
"""

# Installation
# pip install tensorflow

import tensorflow as tf
from tensorflow import keras
from tensorflow.keras import layers, models
import numpy as np
import matplotlib.pyplot as plt

print(f"TensorFlow version: {tf.__version__}")
print(f"Keras version: {keras.__version__}")

# Check GPU
print(f"GPU available: {tf.config.list_physical_devices('GPU')}")

# ═══════════════════════════════════════════
# NEURAL NETWORKS WITH KERAS
# ═══════════════════════════════════════════

# ─────────────────────────────────────────────
# 1. SIMPLE NEURAL NETWORK (MNIST)
# ─────────────────────────────────────────────

# Load data
(X_train, y_train), (X_test, y_test) = keras.datasets.mnist.load_data()

print(f"\nDataset shapes:")
print(f"X_train: {X_train.shape}")
print(f"X_test: {X_test.shape}")

# Preprocess
X_train = X_train.reshape(-1, 784) / 255.0
X_test = X_test.reshape(-1, 784) / 255.0

# One-hot encode labels
y_train_cat = keras.utils.to_categorical(y_train, 10)
y_test_cat = keras.utils.to_categorical(y_test, 10)

# Build model - Sequential API
model = keras.Sequential([
    layers.Dense(128, activation='relu', input_shape=(784,)),
    layers.Dropout(0.2),
    layers.Dense(64, activation='relu'),
    layers.Dropout(0.2),
    layers.Dense(10, activation='softmax')
])

# Compile
model.compile(
    optimizer='adam',
    loss='categorical_crossentropy',
    metrics=['accuracy']
)

# Model summary
print("\n" + "="*60)
print("MODEL ARCHITECTURE")
print("="*60)
model.summary()

# Train
history = model.fit(
    X_train, y_train_cat,
    epochs=5,
    batch_size=128,
    validation_split=0.2,
    verbose=1
)

# Evaluate
test_loss, test_acc = model.evaluate(X_test, y_test_cat)
print(f"\nTest accuracy: {test_acc:.4f}")

# ─────────────────────────────────────────────
# 2. CONVOLUTIONAL NEURAL NETWORK (CNN)
# ─────────────────────────────────────────────

# Load CIFAR-10
(X_train_img, y_train_img), (X_test_img, y_test_img) = keras.datasets.cifar10.load_data()

# Normalize
X_train_img = X_train_img.astype('float32') / 255.0
X_test_img = X_test_img.astype('float32') / 255.0

# One-hot encode
y_train_img = keras.utils.to_categorical(y_train_img, 10)
y_test_img = keras.utils.to_categorical(y_test_img, 10)

# Build CNN
cnn_model = keras.Sequential([
    # Convolutional layers
    layers.Conv2D(32, (3, 3), activation='relu', input_shape=(32, 32, 3)),
    layers.MaxPooling2D((2, 2)),

    layers.Conv2D(64, (3, 3), activation='relu'),
    layers.MaxPooling2D((2, 2)),

    layers.Conv2D(64, (3, 3), activation='relu'),

    # Dense layers
    layers.Flatten(),
    layers.Dense(64, activation='relu'),
    layers.Dropout(0.5),
    layers.Dense(10, activation='softmax')
])

# Compile
cnn_model.compile(
    optimizer='adam',
    loss='categorical_crossentropy',
    metrics=['accuracy']
)

print("\n" + "="*60)
print("CNN ARCHITECTURE")
print("="*60)
cnn_model.summary()

# Train (using subset for demo)
history_cnn = cnn_model.fit(
    X_train_img[:5000], y_train_img[:5000],
    epochs=5,
    batch_size=64,
    validation_split=0.2,
    verbose=1
)

# ─────────────────────────────────────────────
# 3. FUNCTIONAL API (COMPLEX MODELS)
# ─────────────────────────────────────────────

# Multi-input model
input_a = layers.Input(shape=(32,), name='input_a')
input_b = layers.Input(shape=(32,), name='input_b')

# Process first input
x = layers.Dense(16, activation='relu')(input_a)
x = layers.Dropout(0.2)(x)

# Process second input
y = layers.Dense(16, activation='relu')(input_b)
y = layers.Dropout(0.2)(y)

# Concatenate
combined = layers.concatenate([x, y])

# Output layers
z = layers.Dense(32, activation='relu')(combined)
output = layers.Dense(1, activation='sigmoid', name='output')(z)

# Create model
multi_input_model = keras.Model(inputs=[input_a, input_b], outputs=output)

multi_input_model.compile(
    optimizer='adam',
    loss='binary_crossentropy',
    metrics=['accuracy']
)

print("\n" + "="*60)
print("MULTI-INPUT MODEL")
print("="*60)
multi_input_model.summary()

# ═══════════════════════════════════════════
# CALLBACKS
# ═══════════════════════════════════════════

from tensorflow.keras.callbacks import (EarlyStopping, ModelCheckpoint,
                                       ReduceLROnPlateau, TensorBoard)

# Early stopping
early_stop = EarlyStopping(
    monitor='val_loss',
    patience=3,
    restore_best_weights=True
)

# Model checkpoint
checkpoint = ModelCheckpoint(
    'best_model.h5',
    monitor='val_accuracy',
    save_best_only=True,
    mode='max'
)

# Reduce learning rate on plateau
reduce_lr = ReduceLROnPlateau(
    monitor='val_loss',
    factor=0.2,
    patience=2,
    min_lr=0.0001
)

# TensorBoard
tensorboard = TensorBoard(log_dir='./logs', histogram_freq=1)

# Train with callbacks
model_with_callbacks = keras.Sequential([
    layers.Dense(128, activation='relu', input_shape=(784,)),
    layers.Dropout(0.3),
    layers.Dense(64, activation='relu'),
    layers.Dense(10, activation='softmax')
])

model_with_callbacks.compile(
    optimizer='adam',
    loss='categorical_crossentropy',
    metrics=['accuracy']
)

history_callbacks = model_with_callbacks.fit(
    X_train, y_train_cat,
    epochs=20,
    batch_size=128,
    validation_split=0.2,
    callbacks=[early_stop, checkpoint, reduce_lr],
    verbose=0
)

print("\n" + "="*60)
print("TRAINING WITH CALLBACKS")
print("="*60)
print(f"Training stopped at epoch: {len(history_callbacks.history['loss'])}")
print(f"Best validation accuracy: {max(history_callbacks.history['val_accuracy']):.4f}")

# ═══════════════════════════════════════════
# TRANSFER LEARNING
# ═══════════════════════════════════════════

from tensorflow.keras.applications import VGG16, ResNet50, MobileNetV2

# Load pre-trained model
base_model = MobileNetV2(
    weights='imagenet',
    include_top=False,
    input_shape=(224, 224, 3)
)

# Freeze base model
base_model.trainable = False

# Add custom layers
transfer_model = keras.Sequential([
    base_model,
    layers.GlobalAveragePooling2D(),
    layers.Dense(128, activation='relu'),
    layers.Dropout(0.5),
    layers.Dense(10, activation='softmax')  # 10 classes
])

transfer_model.compile(
    optimizer='adam',
    loss='categorical_crossentropy',
    metrics=['accuracy']
)

print("\n" + "="*60)
print("TRANSFER LEARNING MODEL")
print("="*60)
print(f"Total parameters: {transfer_model.count_params():,}")
print(f"Trainable parameters: {sum([tf.size(w).numpy() for w in transfer_model.trainable_weights]):,}")

# ═══════════════════════════════════════════
# CUSTOM TRAINING LOOPS
# ═══════════════════════════════════════════

# Define model
custom_model = keras.Sequential([
    layers.Dense(64, activation='relu', input_shape=(784,)),
    layers.Dense(10, activation='softmax')
])

# Define loss and optimizer
loss_fn = keras.losses.CategoricalCrossentropy()
optimizer = keras.optimizers.Adam(learning_rate=0.001)

# Metrics
train_acc_metric = keras.metrics.CategoricalAccuracy()

# Custom training step
@tf.function
def train_step(x, y):
    with tf.GradientTape() as tape:
        predictions = custom_model(x, training=True)
        loss = loss_fn(y, predictions)

    gradients = tape.gradient(loss, custom_model.trainable_weights)
    optimizer.apply_gradients(zip(gradients, custom_model.trainable_weights))

    train_acc_metric.update_state(y, predictions)
    return loss

# Training loop
epochs = 3
batch_size = 128

print("\n" + "="*60)
print("CUSTOM TRAINING LOOP")
print("="*60)

for epoch in range(epochs):
    print(f"\nEpoch {epoch + 1}/{epochs}")

    # Reset metrics
    train_acc_metric.reset_states()

    # Training
    for i in range(0, len(X_train), batch_size):
        x_batch = X_train[i:i+batch_size]
        y_batch = y_train_cat[i:i+batch_size]

        loss = train_step(x_batch, y_batch)

    # Print metrics
    train_acc = train_acc_metric.result()
    print(f"Training accuracy: {float(train_acc):.4f}")

# ═══════════════════════════════════════════
# MODEL SAVING & LOADING
# ═══════════════════════════════════════════

# Save entire model
model.save('my_model.h5')
model.save('my_model')  # SavedModel format (recommended)

# Load model
loaded_model = keras.models.load_model('my_model.h5')

# Save weights only
model.save_weights('model_weights.h5')

# Load weights
model.load_weights('model_weights.h5')

# Save architecture only
model_json = model.to_json()
with open('model_architecture.json', 'w') as f:
    f.write(model_json)

# Load architecture
with open('model_architecture.json', 'r') as f:
    loaded_model_json = f.read()
loaded_model_from_json = keras.models.model_from_json(loaded_model_json)

print("\n✅ TensorFlow/Keras complete!")
```

---

<div align="center">

## 🔥 PyTorch

</div>

### Research-Friendly Deep Learning 🔬

```python
# ═══════════════════════════════════════════
# PYTORCH FUNDAMENTALS
# ═══════════════════════════════════════════

"""
PyTorch: Facebook's deep learning framework
- Dynamic computation graphs
- Pythonic and intuitive
- Strong research community
- Easy debugging
- Flexible and fast
"""

# Installation
# pip install torch torchvision torchaudio

import torch
import torch.nn as nn
import torch.optim as optim
import torch.nn.functional as F
from torch.utils.data import DataLoader, TensorDataset, Dataset
import torchvision
import torchvision.transforms as transforms
import numpy as np

print(f"PyTorch version: {torch.__version__}")
print(f"CUDA available: {torch.cuda.is_available()}")
if torch.cuda.is_available():
    print(f"CUDA device: {torch.cuda.get_device_name(0)}")

# Set device
device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
print(f"Using device: {device}")

# ═══════════════════════════════════════════
# TENSORS - PYTORCH BASICS
# ═══════════════════════════════════════════

print("\n" + "="*60)
print("TENSOR OPERATIONS")
print("="*60)

# Create tensors
x = torch.tensor([1, 2, 3, 4, 5])
y = torch.zeros(3, 4)
z = torch.ones(2, 3)
random_tensor = torch.randn(3, 3)

print(f"\nTensor x: {x}")
print(f"Tensor shape: {x.shape}")
print(f"Tensor dtype: {x.dtype}")

# Operations
a = torch.tensor([1.0, 2.0, 3.0])
b = torch.tensor([4.0, 5.0, 6.0])

print(f"\nAddition: {a + b}")
print(f"Multiplication: {a * b}")
print(f"Dot product: {torch.dot(a, b)}")

# Matrix operations
matrix_a = torch.randn(3, 4)
matrix_b = torch.randn(4, 2)
result = torch.mm(matrix_a, matrix_b)  # Matrix multiplication
print(f"\nMatrix multiplication shape: {result.shape}")

# Move to GPU (if available)
if torch.cuda.is_available():
    x_gpu = x.to(device)
    print(f"Tensor on GPU: {x_gpu.device}")

# ═══════════════════════════════════════════
# NEURAL NETWORKS
# ═══════════════════════════════════════════

# ─────────────────────────────────────────────
# 1. SIMPLE FEEDFORWARD NETWORK
# ─────────────────────────────────────────────

class SimpleNet(nn.Module):
    def __init__(self, input_size, hidden_size, num_classes):
        super(SimpleNet, self).__init__()
        self.fc1 = nn.Linear(input_size, hidden_size)
        self.relu = nn.ReLU()
        self.fc2 = nn.Linear(hidden_size, num_classes)

    def forward(self, x):
        out = self.fc1(x)
        out = self.relu(out)
        out = self.fc2(out)
        return out

# Initialize model
model = SimpleNet(input_size=784, hidden_size=128, num_classes=10)
model = model.to(device)

print("\n" + "="*60)
print("SIMPLE NEURAL NETWORK")
print("="*60)
print(model)

# Count parameters
total_params = sum(p.numel() for p in model.parameters())
trainable_params = sum(p.numel() for p in model.parameters() if p.requires_grad)
print(f"\nTotal parameters: {total_params:,}")
print(f"Trainable parameters: {trainable_params:,}")

# ─────────────────────────────────────────────
# 2. MNIST CLASSIFICATION
# ─────────────────────────────────────────────

# Load MNIST dataset
transform = transforms.Compose([
    transforms.ToTensor(),
    transforms.Normalize((0.1307,), (0.3081,))
])

train_dataset = torchvision.datasets.MNIST(
    root='./data',
    train=True,
    transform=transform,
    download=True
)

test_dataset = torchvision.datasets.MNIST(
    root='./data',
    train=False,
    transform=transform
)

# Create data loaders
batch_size = 128
train_loader = DataLoader(train_dataset, batch_size=batch_size, shuffle=True)
test_loader = DataLoader(test_dataset, batch_size=batch_size, shuffle=False)

print(f"\nTraining samples: {len(train_dataset)}")
print(f"Test samples: {len(test_dataset)}")

# Define model
class MNISTNet(nn.Module):
    def __init__(self):
        super(MNISTNet, self).__init__()
        self.fc1 = nn.Linear(784, 512)
        self.dropout1 = nn.Dropout(0.2)
        self.fc2 = nn.Linear(512, 256)
        self.dropout2 = nn.Dropout(0.2)
        self.fc3 = nn.Linear(256, 10)

    def forward(self, x):
        x = x.view(-1, 784)  # Flatten
        x = F.relu(self.fc1(x))
        x = self.dropout1(x)
        x = F.relu(self.fc2(x))
        x = self.dropout2(x)
        x = self.fc3(x)
        return x

mnist_model = MNISTNet().to(device)

# Loss and optimizer
criterion = nn.CrossEntropyLoss()
optimizer = optim.Adam(mnist_model.parameters(), lr=0.001)

# Training function
def train(model, device, train_loader, optimizer, epoch):
    model.train()
    train_loss = 0
    correct = 0

    for batch_idx, (data, target) in enumerate(train_loader):
        data, target = data.to(device), target.to(device)

        optimizer.zero_grad()
        output = model(data)
        loss = criterion(output, target)
        loss.backward()
        optimizer.step()

        train_loss += loss.item()
        pred = output.argmax(dim=1, keepdim=True)
        correct += pred.eq(target.view_as(pred)).sum().item()

    train_loss /= len(train_loader)
    accuracy = 100. * correct / len(train_loader.dataset)

    print(f'Epoch {epoch}: Train Loss: {train_loss:.4f}, Accuracy: {accuracy:.2f}%')
    return train_loss, accuracy

# Testing function
def test(model, device, test_loader):
    model.eval()
    test_loss = 0
    correct = 0

    with torch.no_grad():
        for data, target in test_loader:
            data, target = data.to(device), target.to(device)
            output = model(data)
            test_loss += criterion(output, target).item()
            pred = output.argmax(dim=1, keepdim=True)
            correct += pred.eq(target.view_as(pred)).sum().item()

    test_loss /= len(test_loader)
    accuracy = 100. * correct / len(test_loader.dataset)

    print(f'Test Loss: {test_loss:.4f}, Accuracy: {accuracy:.2f}%')
    return test_loss, accuracy

# Train model
print("\n" + "="*60)
print("TRAINING MNIST MODEL")
print("="*60)

epochs = 5
for epoch in range(1, epochs + 1):
    train_loss, train_acc = train(mnist_model, device, train_loader, optimizer, epoch)

# Test model
print("\n" + "="*60)
print("TESTING")
print("="*60)
test_loss, test_acc = test(mnist_model, device, test_loader)

# ─────────────────────────────────────────────
# 3. CONVOLUTIONAL NEURAL NETWORK (CNN)
# ─────────────────────────────────────────────

class CNN(nn.Module):
    def __init__(self):
        super(CNN, self).__init__()
        # Convolutional layers
        self.conv1 = nn.Conv2d(1, 32, kernel_size=3, padding=1)
        self.conv2 = nn.Conv2d(32, 64, kernel_size=3, padding=1)
        self.pool = nn.MaxPool2d(2, 2)

        # Fully connected layers
        self.fc1 = nn.Linear(64 * 7 * 7, 128)
        self.fc2 = nn.Linear(128, 10)

        self.dropout = nn.Dropout(0.5)

    def forward(self, x):
        # Convolutional layers with pooling
        x = self.pool(F.relu(self.conv1(x)))  # 28x28 -> 14x14
        x = self.pool(F.relu(self.conv2(x)))  # 14x14 -> 7x7

        # Flatten
        x = x.view(-1, 64 * 7 * 7)

        # Fully connected layers
        x = F.relu(self.fc1(x))
        x = self.dropout(x)
        x = self.fc2(x)

        return x

cnn_model = CNN().to(device)

print("\n" + "="*60)
print("CNN ARCHITECTURE")
print("="*60)
print(cnn_model)

# ─────────────────────────────────────────────
# 4. RESIDUAL NETWORK (ResNet)
# ─────────────────────────────────────────────

class ResidualBlock(nn.Module):
    def __init__(self, in_channels, out_channels, stride=1):
        super(ResidualBlock, self).__init__()
        self.conv1 = nn.Conv2d(in_channels, out_channels, kernel_size=3,
                              stride=stride, padding=1, bias=False)
        self.bn1 = nn.BatchNorm2d(out_channels)
        self.conv2 = nn.Conv2d(out_channels, out_channels, kernel_size=3,
                              stride=1, padding=1, bias=False)
        self.bn2 = nn.BatchNorm2d(out_channels)

        self.shortcut = nn.Sequential()
        if stride != 1 or in_channels != out_channels:
            self.shortcut = nn.Sequential(
                nn.Conv2d(in_channels, out_channels, kernel_size=1,
                         stride=stride, bias=False),
                nn.BatchNorm2d(out_channels)
            )

    def forward(self, x):
        out = F.relu(self.bn1(self.conv1(x)))
        out = self.bn2(self.conv2(out))
        out += self.shortcut(x)
        out = F.relu(out)
        return out

class SimpleResNet(nn.Module):
    def __init__(self, num_classes=10):
        super(SimpleResNet, self).__init__()
        self.conv1 = nn.Conv2d(3, 64, kernel_size=3, stride=1, padding=1)
        self.bn1 = nn.BatchNorm2d(64)

        self.layer1 = ResidualBlock(64, 64)
        self.layer2 = ResidualBlock(64, 128, stride=2)
        self.layer3 = ResidualBlock(128, 256, stride=2)

        self.avg_pool = nn.AdaptiveAvgPool2d((1, 1))
        self.fc = nn.Linear(256, num_classes)

    def forward(self, x):
        out = F.relu(self.bn1(self.conv1(x)))
        out = self.layer1(out)
        out = self.layer2(out)
        out = self.layer3(out)
        out = self.avg_pool(out)
        out = out.view(out.size(0), -1)
        out = self.fc(out)
        return out

resnet_model = SimpleResNet().to(device)

print("\n" + "="*60)
print("RESNET ARCHITECTURE")
print("="*60)
print(f"Total parameters: {sum(p.numel() for p in resnet_model.parameters()):,}")

# ═══════════════════════════════════════════
# CUSTOM DATASETS
# ═══════════════════════════════════════════

class CustomDataset(Dataset):
    def __init__(self, data, labels, transform=None):
        self.data = data
        self.labels = labels
        self.transform = transform

    def __len__(self):
        return len(self.data)

    def __getitem__(self, idx):
        sample = self.data[idx]
        label = self.labels[idx]

        if self.transform:
            sample = self.transform(sample)

        return sample, label

# Example usage
X = np.random.randn(1000, 28, 28)
y = np.random.randint(0, 10, 1000)

custom_dataset = CustomDataset(X, y, transform=transforms.ToTensor())
custom_loader = DataLoader(custom_dataset, batch_size=32, shuffle=True)

print("\n" + "="*60)
print("CUSTOM DATASET")
print("="*60)
print(f"Dataset size: {len(custom_dataset)}")

# ═══════════════════════════════════════════
# LEARNING RATE SCHEDULING
# ═══════════════════════════════════════════

from torch.optim.lr_scheduler import StepLR, ReduceLROnPlateau, CosineAnnealingLR

model = SimpleNet(784, 128, 10).to(device)
optimizer = optim.Adam(model.parameters(), lr=0.001)

# Step LR: Decay LR by factor every step_size epochs
scheduler_step = StepLR(optimizer, step_size=30, gamma=0.1)

# Reduce on plateau: Reduce when metric stops improving
scheduler_plateau = ReduceLROnPlateau(optimizer, mode='min', factor=0.1, patience=10)

# Cosine annealing
scheduler_cosine = CosineAnnealingLR(optimizer, T_max=200)

print("\n" + "="*60)
print("LEARNING RATE SCHEDULERS")
print("="*60)
print(f"Initial LR: {optimizer.param_groups[0]['lr']}")

# ═══════════════════════════════════════════
# MODEL SAVING & LOADING
# ═══════════════════════════════════════════

# Save entire model
torch.save(mnist_model, 'mnist_model_complete.pth')

# Save model state dict (recommended)
torch.save(mnist_model.state_dict(), 'mnist_model_state.pth')

# Save checkpoint
checkpoint = {
    'epoch': 5,
    'model_state_dict': mnist_model.state_dict(),
    'optimizer_state_dict': optimizer.state_dict(),
    'loss': train_loss,
}
torch.save(checkpoint, 'checkpoint.pth')

# Load model state dict
loaded_model = MNISTNet().to(device)
loaded_model.load_state_dict(torch.load('mnist_model_state.pth'))
loaded_model.eval()

# Load checkpoint
checkpoint = torch.load('checkpoint.pth')
mnist_model.load_state_dict(checkpoint['model_state_dict'])
optimizer.load_state_dict(checkpoint['optimizer_state_dict'])
epoch = checkpoint['epoch']
loss = checkpoint['loss']

print("\n" + "="*60)
print("MODEL PERSISTENCE")
print("="*60)
print(f"Checkpoint loaded: Epoch {epoch}, Loss {loss:.4f}")

# ═══════════════════════════════════════════
# TRANSFER LEARNING
# ═══════════════════════════════════════════

# Load pre-trained ResNet
pretrained_resnet = torchvision.models.resnet18(pretrained=True)

# Freeze all layers
for param in pretrained_resnet.parameters():
    param.requires_grad = False

# Replace final layer
num_features = pretrained_resnet.fc.in_features
pretrained_resnet.fc = nn.Linear(num_features, 10)  # 10 classes

pretrained_resnet = pretrained_resnet.to(device)

print("\n" + "="*60)
print("TRANSFER LEARNING")
print("="*60)
print(f"Total parameters: {sum(p.numel() for p in pretrained_resnet.parameters()):,}")
print(f"Trainable parameters: {sum(p.numel() for p in pretrained_resnet.parameters() if p.requires_grad):,}")

# ═══════════════════════════════════════════
# PYTORCH LIGHTNING (SIMPLIFIED TRAINING)
# ═══════════════════════════════════════════

"""
# Install: pip install pytorch-lightning

import pytorch_lightning as pl

class LitModel(pl.LightningModule):
    def __init__(self):
        super().__init__()
        self.model = MNISTNet()
        self.criterion = nn.CrossEntropyLoss()

    def forward(self, x):
        return self.model(x)

    def training_step(self, batch, batch_idx):
        x, y = batch
        y_hat = self(x)
        loss = self.criterion(y_hat, y)
        self.log('train_loss', loss)
        return loss

    def validation_step(self, batch, batch_idx):
        x, y = batch
        y_hat = self(x)
        loss = self.criterion(y_hat, y)
        acc = (y_hat.argmax(dim=1) == y).float().mean()
        self.log('val_loss', loss)
        self.log('val_acc', acc)

    def configure_optimizers(self):
        return optim.Adam(self.parameters(), lr=0.001)

# Train
lit_model = LitModel()
trainer = pl.Trainer(max_epochs=5, gpus=1 if torch.cuda.is_available() else 0)
trainer.fit(lit_model, train_loader, test_loader)
"""

print("\n✅ PyTorch complete!")
```

---

<div align="center">

## ⚡ Gradient Boosting

</div>

### XGBoost, LightGBM, CatBoost 🚀

```python
# ═══════════════════════════════════════════
# GRADIENT BOOSTING FRAMEWORKS
# ═══════════════════════════════════════════

"""
Gradient Boosting: Ensemble learning technique
- XGBoost: Most popular, Kaggle winner
- LightGBM: Microsoft, fastest
- CatBoost: Yandex, handles categorical features
"""

# Installation
# pip install xgboost lightgbm catboost

import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score, mean_squared_error
from sklearn.datasets import load_breast_cancer, load_diabetes

# ═══════════════════════════════════════════
# XGBOOST
# ═══════════════════════════════════════════

import xgboost as xgb
from xgboost import XGBClassifier, XGBRegressor

print("="*60)
print("XGBOOST")
print("="*60)
print(f"XGBoost version: {xgb.__version__}")

# ─────────────────────────────────────────────
# Classification with XGBoost
# ─────────────────────────────────────────────

# Load data
data = load_breast_cancer()
X, y = data.data, data.target
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

# Method 1: Scikit-learn API
xgb_clf = XGBClassifier(
    n_estimators=100,
    max_depth=3,
    learning_rate=0.1,
    random_state=42,
    eval_metric='logloss'
)

xgb_clf.fit(X_train, y_train)
y_pred = xgb_clf.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)

print(f"\nXGBoost Classifier Accuracy: {accuracy:.4f}")

# Method 2: Native API (more features)
dtrain = xgb.DMatrix(X_train, label=y_train)
dtest = xgb.DMatrix(X_test, label=y_test)

params = {
    'objective': 'binary:logistic',
    'max_depth': 3,
    'learning_rate': 0.1,
    'eval_metric': 'logloss'
}

# Train with early stopping
evals = [(dtrain, 'train'), (dtest, 'test')]
bst = xgb.train(
    params,
    dtrain,
    num_boost_round=100,
    evals=evals,
    early_stopping_rounds=10,
    verbose_eval=False
)

print(f"Best iteration: {bst.best_iteration}")
print(f"Best score: {bst.best_score:.4f}")

# Feature importance
feature_importance = xgb_clf.feature_importances_
top_features = sorted(zip(data.feature_names, feature_importance),
                     key=lambda x: x[1], reverse=True)[:5]
print("\nTop 5 Features:")
for feat, imp in top_features:
    print(f"  {feat}: {imp:.4f}")

# ─────────────────────────────────────────────
# Regression with XGBoost
# ─────────────────────────────────────────────

diabetes = load_diabetes()
X_reg, y_reg = diabetes.data, diabetes.target
X_train_reg, X_test_reg, y_train_reg, y_test_reg = train_test_split(
    X_reg, y_reg, test_size=0.2, random_state=42
)

xgb_reg = XGBRegressor(
    n_estimators=100,
    max_depth=3,
    learning_rate=0.1,
    random_state=42
)

xgb_reg.fit(X_train_reg, y_train_reg)
y_pred_reg = xgb_reg.predict(X_test_reg)
rmse = np.sqrt(mean_squared_error(y_test_reg, y_pred_reg))

print(f"\nXGBoost Regressor RMSE: {rmse:.2f}")

# ═══════════════════════════════════════════
# LIGHTGBM
# ═══════════════════════════════════════════

import lightgbm as lgb
from lightgbm import LGBMClassifier, LGBMRegressor

print("\n" + "="*60)
print("LIGHTGBM")
print("="*60)
print(f"LightGBM version: {lgb.__version__}")

# ─────────────────────────────────────────────
# Classification with LightGBM
# ─────────────────────────────────────────────

# Method 1: Scikit-learn API
lgb_clf = LGBMClassifier(
    n_estimators=100,
    max_depth=3,
    learning_rate=0.1,
    random_state=42
)

lgb_clf.fit(X_train, y_train)
y_pred_lgb = lgb_clf.predict(X_test)
accuracy_lgb = accuracy_score(y_test, y_pred_lgb)

print(f"\nLightGBM Classifier Accuracy: {accuracy_lgb:.4f}")

# Method 2: Native API
train_data = lgb.Dataset(X_train, label=y_train)
test_data = lgb.Dataset(X_test, label=y_test, reference=train_data)

params_lgb = {
    'objective': 'binary',
    'metric': 'binary_logloss',
    'max_depth': 3,
    'learning_rate': 0.1,
    'verbose': -1
}

# Train with validation
gbm = lgb.train(
    params_lgb,
    train_data,
    num_boost_round=100,
    valid_sets=[test_data],
    callbacks=[lgb.early_stopping(stopping_rounds=10)]
)

print(f"Best iteration: {gbm.best_iteration}")

# ─────────────────────────────────────────────
# Regression with LightGBM
# ─────────────────────────────────────────────

lgb_reg = LGBMRegressor(
    n_estimators=100,
    max_depth=3,
    learning_rate=0.1,
    random_state=42
)

lgb_reg.fit(X_train_reg, y_train_reg)
y_pred_lgb_reg = lgb_reg.predict(X_test_reg)
rmse_lgb = np.sqrt(mean_squared_error(y_test_reg, y_pred_lgb_reg))

print(f"\nLightGBM Regressor RMSE: {rmse_lgb:.2f}")

# ═══════════════════════════════════════════
# CATBOOST
# ═══════════════════════════════════════════

from catboost import CatBoostClassifier, CatBoostRegressor, Pool

print("\n" + "="*60)
print("CATBOOST")
print("="*60)

# ─────────────────────────────────────────────
# Classification with CatBoost
# ─────────────────────────────────────────────

cat_clf = CatBoostClassifier(
    iterations=100,
    depth=3,
    learning_rate=0.1,
    random_state=42,
    verbose=False
)

cat_clf.fit(X_train, y_train)
y_pred_cat = cat_clf.predict(X_test)
accuracy_cat = accuracy_score(y_test, y_pred_cat)

print(f"\nCatBoost Classifier Accuracy: {accuracy_cat:.4f}")

# With categorical features
df_cat = pd.DataFrame({
    'feature1': np.random.randn(1000),
    'feature2': np.random.randn(1000),
    'category': np.random.choice(['A', 'B', 'C'], 1000),
    'target': np.random.randint(0, 2, 1000)
})

X_cat = df_cat[['feature1', 'feature2', 'category']]
y_cat = df_cat['target']
X_train_cat, X_test_cat, y_train_cat, y_test_cat = train_test_split(
    X_cat, y_cat, test_size=0.2, random_state=42
)

# Specify categorical features
cat_features = ['category']

cat_clf_cat = CatBoostClassifier(
    iterations=100,
    depth=3,
    learning_rate=0.1,
    cat_features=cat_features,
    random_state=42,
    verbose=False
)

cat_clf_cat.fit(X_train_cat, y_train_cat)
y_pred_cat_feat = cat_clf_cat.predict(X_test_cat)
accuracy_cat_feat = accuracy_score(y_test_cat, y_pred_cat_feat)

print(f"CatBoost with Categorical Features Accuracy: {accuracy_cat_feat:.4f}")

# ─────────────────────────────────────────────
# Regression with CatBoost
# ─────────────────────────────────────────────

cat_reg = CatBoostRegressor(
    iterations=100,
    depth=3,
    learning_rate=0.1,
    random_state=42,
    verbose=False
)

cat_reg.fit(X_train_reg, y_train_reg)
y_pred_cat_reg = cat_reg.predict(X_test_reg)
rmse_cat = np.sqrt(mean_squared_error(y_test_reg, y_pred_cat_reg))

print(f"\nCatBoost Regressor RMSE: {rmse_cat:.2f}")

# ═══════════════════════════════════════════
# COMPARISON
# ═══════════════════════════════════════════

print("\n" + "="*60)
print("GRADIENT BOOSTING COMPARISON")
print("="*60)

comparison = pd.DataFrame({
    'Framework': ['XGBoost', 'LightGBM', 'CatBoost'],
    'Classification Accuracy': [accuracy, accuracy_lgb, accuracy_cat],
    'Regression RMSE': [rmse, rmse_lgb, rmse_cat]
})

print("\n", comparison.to_string(index=False))

# ═══════════════════════════════════════════
# HYPERPARAMETER TUNING
# ═══════════════════════════════════════════

from sklearn.model_selection import RandomizedSearchCV

print("\n" + "="*60)
print("HYPERPARAMETER TUNING - XGBOOST")
print("="*60)

param_dist = {
    'n_estimators': [50, 100, 200],
    'max_depth': [3, 5, 7],
    'learning_rate': [0.01, 0.1, 0.3],
    'subsample': [0.7, 0.8, 0.9],
    'colsample_bytree': [0.7, 0.8, 0.9]
}

xgb_search = RandomizedSearchCV(
    XGBClassifier(random_state=42, eval_metric='logloss'),
    param_dist,
    n_iter=10,
    cv=3,
    random_state=42,
    n_jobs=-1
)

xgb_search.fit(X_train, y_train)

print(f"\nBest parameters: {xgb_search.best_params_}")
print(f"Best CV score: {xgb_search.best_score_:.4f}")
print(f"Test score: {xgb_search.score(X_test, y_test):.4f}")

print("\n✅ Gradient Boosting complete!")
```

---

<div align="center">

## 🌟 Other Frameworks

</div>

### Specialized ML Frameworks 🛠️

```python
# ═══════════════════════════════════════════
# OTHER POPULAR ML FRAMEWORKS
# ═══════════════════════════════════════════

# ─────────────────────────────────────────────
# 1. FASTAI - HIGH-LEVEL DEEP LEARNING
# ─────────────────────────────────────────────

"""
# Install: pip install fastai

from fastai.vision.all import *

# Load data
path = untar_data(URLs.PETS)
dls = ImageDataLoaders.from_name_func(
    path, get_image_files(path/'images'),
    valid_pct=0.2,
    label_func=lambda x: x[0].isupper(),
    item_tfms=Resize(224)
)

# Create learner
learn = cnn_learner(dls, resnet34, metrics=error_rate)

# Train
learn.fine_tune(2)

# Predict
img = PILImage.create('dog.jpg')
pred, idx, probs = learn.predict(img)
print(f'Prediction: {pred}; Probability: {probs[idx]:.04f}')
"""

print("FastAI: Simplified deep learning API on top of PyTorch")

# ─────────────────────────────────────────────
# 2. HUGGING FACE TRANSFORMERS - NLP
# ─────────────────────────────────────────────

"""
# Install: pip install transformers

from transformers import pipeline, AutoTokenizer, AutoModelForSequenceClassification

# Sentiment analysis
classifier = pipeline('sentiment-analysis')
result = classifier("I love this product!")
print(result)

# Text generation
generator = pipeline('text-generation', model='gpt2')
text = generator("Once upon a time", max_length=50)
print(text)

# Named Entity Recognition
ner = pipeline('ner', grouped_entities=True)
entities = ner("Elon Musk founded Tesla in California")
print(entities)

# Question Answering
qa = pipeline('question-answering')
context = "Python is a programming language"
question = "What is Python?"
answer = qa(question=question, context=context)
print(answer)
"""

print("\nHugging Face: State-of-the-art NLP with transformers")

# ─────────────────────────────────────────────
# 3. JAX - HIGH-PERFORMANCE ML
# ─────────────────────────────────────────────

"""
# Install: pip install jax jaxlib

import jax
import jax.numpy as jnp
from jax import grad, jit, vmap

# Automatic differentiation
def f(x):
    return jnp.sum(x ** 2)

grad_f = grad(f)
print(grad_f(jnp.array([1.0, 2.0, 3.0])))

# JIT compilation
@jit
def fast_function(x):
    return jnp.sum(x ** 2)

# Vectorization
@vmap
def batch_function(x):
    return jnp.sum(x ** 2)
"""

print("JAX: High-performance numerical computing")

# ─────────────────────────────────────────────
# 4. OPTUNA - HYPERPARAMETER OPTIMIZATION
# ─────────────────────────────────────────────

"""
# Install: pip install optuna

import optuna
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score

def objective(trial):
    n_estimators = trial.suggest_int('n_estimators', 50, 300)
    max_depth = trial.suggest_int('max_depth', 2, 32)

    model = RandomForestClassifier(
        n_estimators=n_estimators,
        max_depth=max_depth,
        random_state=42
    )

    model.fit(X_train, y_train)
    y_pred = model.predict(X_test)
    accuracy = accuracy_score(y_test, y_pred)

    return accuracy

study = optuna.create_study(direction='maximize')
study.optimize(objective, n_trials=50)

print(f'Best parameters: {study.best_params}')
print(f'Best accuracy: {study.best_value:.4f}')
"""

print("Optuna: Automated hyperparameter optimization")

# ─────────────────────────────────────────────
# 5. AUTOKERAS - AUTOML
# ─────────────────────────────────────────────

"""
# Install: pip install autokeras

import autokeras as ak

# Image classification
clf = ak.ImageClassifier(max_trials=10)
clf.fit(x_train, y_train, epochs=10)
accuracy = clf.evaluate(x_test, y_test)

# Text classification
clf_text = ak.TextClassifier(max_trials=10)
clf_text.fit(x_text_train, y_text_train, epochs=10)
"""

print("AutoKeras: Automated machine learning")

# ─────────────────────────────────────────────
# 6. SHAP - MODEL INTERPRETATION
# ─────────────────────────────────────────────

"""
# Install: pip install shap

import shap

# Train model
model = xgb.XGBClassifier()
model.fit(X_train, y_train)

# Explain predictions
explainer = shap.TreeExplainer(model)
shap_values = explainer.shap_values(X_test)

# Visualize
shap.summary_plot(shap_values, X_test)
shap.force_plot(explainer.expected_value, shap_values[0], X_test.iloc[0])
"""

print("SHAP: Model interpretability and explainability")

print("\n✅ Other frameworks overview complete!")
```

---

<div align="center">

## 📊 Framework Comparison

</div>

### Choosing the Right Framework 🎯

```bash
# ═══════════════════════════════════════════
# DETAILED FRAMEWORK COMPARISON
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CLASSICAL ML FRAMEWORKS                  ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Aspect            | Scikit-learn | XGBoost   | LightGBM  | CatBoost |
| ----------------- | ------------ | --------- | --------- | -------- |
| **Speed**         | ⭐⭐         | ⭐⭐⭐    | ⭐⭐⭐⭐  | ⭐⭐⭐   |
| **Accuracy**      | ⭐⭐⭐       | ⭐⭐⭐⭐  | ⭐⭐⭐⭐  | ⭐⭐⭐⭐ |
| **Memory**        | ⭐⭐⭐⭐     | ⭐⭐⭐    | ⭐⭐⭐⭐  | ⭐⭐⭐   |
| **Ease of Use**   | ⭐⭐⭐⭐     | ⭐⭐⭐    | ⭐⭐⭐    | ⭐⭐⭐⭐ |
| **Documentation** | ⭐⭐⭐⭐     | ⭐⭐⭐⭐  | ⭐⭐⭐    | ⭐⭐⭐   |
| **Small Data**    | ✅ Best      | ✅ Good   | ✅ Good   | ✅ Good  |
| **Large Data**    | ❌ Slow      | ✅ Good   | ✅ Best   | ✅ Good  |
| **Categorical**   | ⚠️ Manual    | ⚠️ Manual | ⚠️ Manual | ✅ Auto  |
| **GPU Support**   | ❌ No        | ✅ Yes    | ✅ Yes    | ✅ Yes   |
| **Parallel**      | ✅ Yes       | ✅ Yes    | ✅ Yes    | ✅ Yes   |

</div>

```bash
╔════════════════════════════════════════════════════════════╗
║                   DEEP LEARNING FRAMEWORKS                 ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Aspect             | TensorFlow     | PyTorch        | Keras     | FastAI      |
| ------------------ | -------------- | -------------- | --------- | ----------- |
| **Learning Curve** | ⭐⭐           | ⭐⭐⭐         | ⭐⭐⭐⭐  | ⭐⭐⭐⭐    |
| **Flexibility**    | ⭐⭐⭐⭐       | ⭐⭐⭐⭐       | ⭐⭐⭐    | ⭐⭐        |
| **Production**     | ⭐⭐⭐⭐       | ⭐⭐⭐         | ⭐⭐⭐⭐  | ⭐⭐        |
| **Research**       | ⭐⭐⭐         | ⭐⭐⭐⭐       | ⭐⭐      | ⭐⭐⭐      |
| **Community**      | ⭐⭐⭐⭐       | ⭐⭐⭐⭐       | ⭐⭐⭐⭐  | ⭐⭐⭐      |
| **Mobile**         | ✅ TF Lite     | ⚠️ Limited     | ✅ Via TF | ❌ No       |
| **Web**            | ✅ TF.js       | ⚠️ Limited     | ✅ Via TF | ❌ No       |
| **Debugging**      | ⭐⭐           | ⭐⭐⭐⭐       | ⭐⭐⭐    | ⭐⭐⭐      |
| **Visualization**  | ✅ TensorBoard | ✅ TensorBoard | ✅ Good   | ✅ Built-in |
| **Pre-trained**    | ✅ TF Hub      | ✅ torchvision | ✅ Many   | ✅ Many     |

</div>

```bash
╔════════════════════════════════════════════════════════════╗
║                   USE CASE RECOMMENDATIONS                 ║
╚════════════════════════════════════════════════════════════╝

Tabular Data (Structured):
─────────────────────────────────────────────────────────────
Small datasets (<10K rows):
  1st Choice: Scikit-learn
  2nd Choice: XGBoost
  Why: Simple, fast training, interpretable

Medium datasets (10K-100K):
  1st Choice: XGBoost
  2nd Choice: LightGBM
  Why: Better accuracy, reasonable speed

Large datasets (>100K rows):
  1st Choice: LightGBM
  2nd Choice: CatBoost
  Why: Fastest training, memory efficient

Many categorical features:
  1st Choice: CatBoost
  2nd Choice: LightGBM
  Why: Automatic handling, no encoding needed

Images:
─────────────────────────────────────────────────────────────
Quick prototyping:
  1st Choice: FastAI
  2nd Choice: Keras
  Why: High-level API, quick results

Custom architectures:
  1st Choice: PyTorch
  2nd Choice: TensorFlow
  Why: Full control, easy debugging

Production deployment:
  1st Choice: TensorFlow
  2nd Choice: PyTorch
  Why: TF Serving, TF Lite, mature tools

Mobile/Edge devices:
  1st Choice: TensorFlow Lite
  2nd Choice: ONNX
  Why: Optimized for mobile, small size

Text/NLP:
─────────────────────────────────────────────────────────────
Modern NLP (Transformers):
  1st Choice: Hugging Face
  2nd Choice: PyTorch
  Why: Pre-trained models, easy fine-tuning

Classical NLP:
  1st Choice: Scikit-learn
  2nd Choice: spaCy
  Why: Simple, fast, good for basic tasks

Custom models:
  1st Choice: PyTorch
  2nd Choice: TensorFlow
  Why: Flexibility, research-friendly

Time Series:
─────────────────────────────────────────────────────────────
Traditional forecasting:
  1st Choice: Statsmodels
  2nd Choice: Prophet
  Why: Statistical methods, interpretable

Complex patterns:
  1st Choice: LightGBM
  2nd Choice: LSTM (PyTorch/TF)
  Why: Captures non-linear patterns

Large-scale:
  1st Choice: LightGBM
  2nd Choice: XGBoost
  Why: Fast, handles large datasets

Research:
─────────────────────────────────────────────────────────────
1st Choice: PyTorch
2nd Choice: JAX
Why: Dynamic graphs, easy debugging, Pythonic

Industry/Production:
─────────────────────────────────────────────────────────────
1st Choice: TensorFlow
2nd Choice: XGBoost
Why: Production tools, deployment, serving

Learning/Education:
─────────────────────────────────────────────────────────────
1st Choice: Scikit-learn
2nd Choice: Keras
Why: Simple API, great documentation

Competitions (Kaggle):
─────────────────────────────────────────────────────────────
1st Choice: XGBoost
2nd Choice: LightGBM
Why: Consistently win, ensemble-friendly

╔════════════════════════════════════════════════════════════╗
║                   FRAMEWORK ECOSYSTEM                      ║
╚════════════════════════════════════════════════════════════╝

TensorFlow Ecosystem:
─────────────────────────────────────────────────────────────
• TensorFlow Core: Main framework
• Keras: High-level API
• TensorFlow Lite: Mobile deployment
• TensorFlow.js: Web deployment
• TensorFlow Serving: Production serving
• TensorFlow Extended (TFX): ML pipelines
• TensorBoard: Visualization

PyTorch Ecosystem:
─────────────────────────────────────────────────────────────
• PyTorch Core: Main framework
• torchvision: Computer vision
• torchaudio: Audio processing
• torchtext: NLP utilities
• PyTorch Lightning: High-level wrapper
• TorchServe: Model serving
• ONNX: Model export

Scikit-learn Compatible:
─────────────────────────────────────────────────────────────
• XGBoost: Gradient boosting
• LightGBM: Fast gradient boosting
• CatBoost: Categorical boosting
• Imbalanced-learn: Class imbalance
• Feature-engine: Feature engineering

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🚀 Model Deployment

</div>

### From Training to Production 🏭

```python
# ═══════════════════════════════════════════
# MODEL DEPLOYMENT STRATEGIES
# ═══════════════════════════════════════════

# ─────────────────────────────────────────────
# 1. FLASK API (SIMPLE REST API)
# ─────────────────────────────────────────────

"""
# app.py
from flask import Flask, request, jsonify
import joblib
import numpy as np

app = Flask(__name__)

# Load model at startup
model = joblib.load('model.pkl')

@app.route('/predict', methods=['POST'])
def predict():
    data = request.get_json()
    features = np.array(data['features']).reshape(1, -1)
    prediction = model.predict(features)
    probability = model.predict_proba(features)

    return jsonify({
        'prediction': int(prediction[0]),
        'probability': float(probability[0][1])
    })

@app.route('/health', methods=['GET'])
def health():
    return jsonify({'status': 'healthy'})

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)

# Run: python app.py
# Test: curl -X POST http://localhost:5000/predict -H "Content-Type: application/json" -d '{"features": [1, 2, 3, 4]}'
"""

# ─────────────────────────────────────────────
# 2. FASTAPI (MODERN ASYNC API)
# ─────────────────────────────────────────────

"""
# main.py
from fastapi import FastAPI
from pydantic import BaseModel
import joblib
import numpy as np

app = FastAPI()

# Load model
model = joblib.load('model.pkl')

class PredictionInput(BaseModel):
    features: list

class PredictionOutput(BaseModel):
    prediction: int
    probability: float

@app.post('/predict', response_model=PredictionOutput)
async def predict(input_data: PredictionInput):
    features = np.array(input_data.features).reshape(1, -1)
    prediction = model.predict(features)
    probability = model.predict_proba(features)

    return {
        'prediction': int(prediction[0]),
        'probability': float(probability[0][1])
    }

@app.get('/health')
async def health():
    return {'status': 'healthy'}

# Run: uvicorn main:app --reload
# Docs: http://localhost:8000/docs
"""

# ─────────────────────────────────────────────
# 3. TENSORFLOW SERVING
# ─────────────────────────────────────────────

"""
# Save model in TensorFlow SavedModel format
import tensorflow as tf

model.save('saved_model/1')  # Version 1

# Docker:
docker run -p 8501:8501 \
  --mount type=bind,source=/path/to/saved_model,target=/models/model \
  -e MODEL_NAME=model \
  tensorflow/serving

# Client request:
import requests
import json

data = json.dumps({
    'signature_name': 'serving_default',
    'instances': [[1.0, 2.0, 3.0, 4.0]]
})

headers = {'content-type': 'application/json'}
response = requests.post(
    'http://localhost:8501/v1/models/model:predict',
    data=data,
    headers=headers
)

predictions = response.json()
"""

# ─────────────────────────────────────────────
# 4. TORCHSERVE (PYTORCH SERVING)
# ─────────────────────────────────────────────

"""
# Install TorchServe
pip install torchserve torch-model-archiver

# Archive model
torch-model-archiver \
  --model-name mnist \
  --version 1.0 \
  --model-file model.py \
  --serialized-file model.pth \
  --handler image_classifier

# Start server
torchserve --start --model-store model_store --models mnist=mnist.mar

# Predict
curl http://localhost:8080/predictions/mnist -T image.jpg
"""

# ─────────────────────────────────────────────
# 5. DOCKER DEPLOYMENT
# ─────────────────────────────────────────────

"""
# Dockerfile
FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 5000

CMD ["python", "app.py"]

# Build:
docker build -t ml-model-api .

# Run:
docker run -p 5000:5000 ml-model-api

# Docker Compose (docker-compose.yml):
version: '3.8'
services:
  api:
    build: .
    ports:
      - "5000:5000"
    environment:
      - MODEL_PATH=/models/model.pkl
    volumes:
      - ./models:/models
"""

# ─────────────────────────────────────────────
# 6. CLOUD DEPLOYMENT
# ─────────────────────────────────────────────

"""
# AWS SageMaker:
import sagemaker
from sagemaker.sklearn import SKLearnModel

sklearn_model = SKLearnModel(
    model_data='s3://bucket/model.tar.gz',
    role=role,
    entry_point='inference.py',
    framework_version='0.23-1'
)

predictor = sklearn_model.deploy(
    initial_instance_count=1,
    instance_type='ml.m5.large'
)

# Google Cloud AI Platform:
gcloud ai-platform models create model_name \
  --regions us-central1

gcloud ai-platform versions create v1 \
  --model model_name \
  --runtime-version 2.8 \
  --python-version 3.7 \
  --framework scikit-learn \
  --package-uris gs://bucket/model.tar.gz

# Azure ML:
from azureml.core import Workspace, Model

ws = Workspace.from_config()

model = Model.register(
    workspace=ws,
    model_path='model.pkl',
    model_name='my-model'
)

service = Model.deploy(
    workspace=ws,
    name='my-service',
    models=[model],
    inference_config=inference_config,
    deployment_config=deployment_config
)
"""

# ─────────────────────────────────────────────
# 7. EDGE DEPLOYMENT (MOBILE)
# ─────────────────────────────────────────────

"""
# TensorFlow Lite conversion:
import tensorflow as tf

converter = tf.lite.TFLiteConverter.from_saved_model('saved_model')
converter.optimizations = [tf.lite.Optimize.DEFAULT]
tflite_model = converter.convert()

with open('model.tflite', 'wb') as f:
    f.write(tflite_model)

# ONNX export (PyTorch):
import torch.onnx

dummy_input = torch.randn(1, 3, 224, 224)
torch.onnx.export(
    model,
    dummy_input,
    'model.onnx',
    export_params=True,
    opset_version=11,
    input_names=['input'],
    output_names=['output']
)

# Core ML (iOS):
import coremltools as ct

coreml_model = ct.convert(
    model,
    inputs=[ct.ImageType(shape=(1, 224, 224, 3))]
)
coreml_model.save('model.mlmodel')
"""

# ─────────────────────────────────────────────
# 8. BATCH PREDICTION
# ─────────────────────────────────────────────

"""
# batch_predict.py
import pandas as pd
import joblib

def batch_predict(input_file, output_file, model_path):
    # Load model
    model = joblib.load(model_path)

    # Load data
    df = pd.read_csv(input_file)

    # Make predictions
    X = df.drop(['id'], axis=1)
    predictions = model.predict(X)
    probabilities = model.predict_proba(X)

    # Save results
    results = pd.DataFrame({
        'id': df['id'],
        'prediction': predictions,
        'probability': probabilities[:, 1]
    })

    results.to_csv(output_file, index=False)
    print(f'Predictions saved to {output_file}')

if __name__ == '__main__':
    batch_predict('input.csv', 'output.csv', 'model.pkl')

# Airflow DAG for scheduling:
from airflow import DAG
from airflow.operators.python import PythonOperator
from datetime import datetime

dag = DAG(
    'batch_prediction',
    start_date=datetime(2024, 1, 1),
    schedule_interval='@daily'
)

predict_task = PythonOperator(
    task_id='batch_predict',
    python_callable=batch_predict,
    dag=dag
)
"""

# ─────────────────────────────────────────────
# 9. MODEL MONITORING
# ─────────────────────────────────────────────

"""
# monitoring.py
import logging
from prometheus_client import Counter, Histogram
import time

# Metrics
prediction_counter = Counter('predictions_total', 'Total predictions')
prediction_latency = Histogram('prediction_latency_seconds', 'Prediction latency')
prediction_errors = Counter('prediction_errors_total', 'Total prediction errors')

def predict_with_monitoring(features):
    prediction_counter.inc()

    start_time = time.time()
    try:
        prediction = model.predict(features)
        latency = time.time() - start_time
        prediction_latency.observe(latency)

        # Log prediction
        logging.info(f'Prediction: {prediction}, Latency: {latency:.3f}s')

        return prediction
    except Exception as e:
        prediction_errors.inc()
        logging.error(f'Prediction error: {str(e)}')
        raise

# Data drift detection:
from scipy.stats import ks_2samp

def check_data_drift(reference_data, new_data, threshold=0.05):
    drift_detected = {}

    for column in reference_data.columns:
        statistic, p_value = ks_2samp(reference_data[column], new_data[column])
        drift_detected[column] = p_value < threshold

        if drift_detected[column]:
            logging.warning(f'Data drift detected in column: {column}')

    return drift_detected
"""

print("\n✅ Model deployment strategies complete!")
```

---

<div align="center">

## 💡 Best Practices

</div>

### Professional ML Development 📋

```bash
# ═══════════════════════════════════════════
# ML DEVELOPMENT BEST PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PROJECT ORGANIZATION                     ║
╚════════════════════════════════════════════════════════════╝

Recommended Structure:
─────────────────────────────────────────────────────────────
ml-project/
├── data/
│   ├── raw/              # Original, immutable data
│   ├── processed/        # Cleaned, processed data
│   └── features/         # Feature engineered data
├── notebooks/
│   ├── 01_eda.ipynb
│   ├── 02_baseline.ipynb
│   └── 03_experiments.ipynb
├── src/
│   ├── __init__.py
│   ├── data/
│   │   ├── __init__.py
│   │   └── preprocessing.py
│   ├── features/
│   │   ├── __init__.py
│   │   └── engineering.py
│   ├── models/
│   │   ├── __init__.py
│   │   ├── train.py
│   │   └── predict.py
│   └── utils/
│       ├── __init__.py
│       └── metrics.py
├── models/               # Trained models
├── reports/              # Reports and visualizations
├── tests/                # Unit tests
├── configs/              # Configuration files
├── requirements.txt
├── setup.py
└── README.md

╔════════════════════════════════════════════════════════════╗
║                   DATA MANAGEMENT                          ║
╚════════════════════════════════════════════════════════════╝

✅ DO:
─────────────────────────────────────────────────────────────
• Keep raw data immutable
• Version your datasets (DVC, Git LFS)
• Document data sources and transformations
• Validate data quality
• Handle missing values explicitly
• Split data properly (train/val/test)
• Use stratified splits for imbalanced data
• Set random seeds for reproducibility
• Check for data leakage
• Monitor data drift in production

❌ DON'T:
─────────────────────────────────────────────────────────────
• Modify raw data files
• Mix train and test data
• Forget to scale/normalize
• Ignore class imbalance
• Overfit to validation set
• Use test set for development

Example Data Pipeline:
─────────────────────────────────────────────────────────────
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
import joblib

def prepare_data(data_path, test_size=0.2, random_state=42):
    # Load data
    df = pd.read_csv(data_path)

    # Validate
    assert not df.isnull().all().any(), "Column with all NaN"
    assert len(df) > 0, "Empty dataset"

    # Split features and target
    X = df.drop('target', axis=1)
    y = df['target']

    # Train/test split
    X_train, X_test, y_train, y_test = train_test_split(
        X, y, test_size=test_size,
        random_state=random_state,
        stratify=y  # Maintain class distribution
    )

    # Scale features
    scaler = StandardScaler()
    X_train_scaled = scaler.fit_transform(X_train)
    X_test_scaled = scaler.transform(X_test)

    # Save scaler
    joblib.dump(scaler, 'scaler.pkl')

    return X_train_scaled, X_test_scaled, y_train, y_test

╔════════════════════════════════════════════════════════════╗
║                   MODEL DEVELOPMENT                        ║
╚════════════════════════════════════════════════════════════╝

Development Workflow:
─────────────────────────────────────────────────────────────
1. Start with baseline model (simple)
2. Establish evaluation metrics
3. Experiment with features
4. Try different algorithms
5. Tune hyperparameters
6. Ensemble models
7. Evaluate on test set (once!)

✅ Best Practices:
─────────────────────────────────────────────────────────────
• Use cross-validation
• Track experiments (MLflow, Weights & Biases)
• Compare multiple models
• Tune hyperparameters systematically
• Use early stopping
• Save best models
• Document model architecture
• Version control models
• Test on holdout set last
• Monitor training curves

Example Training Pipeline:
─────────────────────────────────────────────────────────────
from sklearn.model_selection import cross_val_score
from sklearn.ensemble import RandomForestClassifier
import mlflow

def train_model(X_train, y_train, params):
    with mlflow.start_run():
        # Log parameters
        mlflow.log_params(params)

        # Train model
        model = RandomForestClassifier(**params)
        model.fit(X_train, y_train)

        # Cross-validation
        cv_scores = cross_val_score(model, X_train, y_train, cv=5)

        # Log metrics
        mlflow.log_metric('cv_mean', cv_scores.mean())
        mlflow.log_metric('cv_std', cv_scores.std())

        # Save model
        mlflow.sklearn.log_model(model, 'model')

        return model, cv_scores

╔════════════════════════════════════════════════════════════╗
║                   MODEL EVALUATION                         ║
╚════════════════════════════════════════════════════════════╝

Evaluation Checklist:
─────────────────────────────────────────────────────────────
☐ Multiple metrics (accuracy, precision, recall, F1, AUC)
☐ Confusion matrix
☐ ROC/PR curves
☐ Cross-validation scores
☐ Feature importance
☐ Error analysis
☐ Bias/fairness checks
☐ Performance across subgroups
☐ Computational cost
☐ Inference time

Example Evaluation:
─────────────────────────────────────────────────────────────
from sklearn.metrics import (classification_report,
                             confusion_matrix, roc_auc_score)
import matplotlib.pyplot as plt
import seaborn as sns

def evaluate_model(model, X_test, y_test):
    # Predictions
    y_pred = model.predict(X_test)
    y_pred_proba = model.predict_proba(X_test)[:, 1]

    # Metrics
    print("Classification Report:")
    print(classification_report(y_test, y_pred))

    # Confusion Matrix
    cm = confusion_matrix(y_test, y_pred)
    plt.figure(figsize=(8, 6))
    sns.heatmap(cm, annot=True, fmt='d', cmap='Blues')
    plt.title('Confusion Matrix')
    plt.ylabel('True Label')
    plt.xlabel('Predicted Label')
    plt.savefig('confusion_matrix.png')

    # AUC-ROC
    auc = roc_auc_score(y_test, y_pred_proba)
    print(f"\nAUC-ROC: {auc:.4f}")

    # Feature Importance
    if hasattr(model, 'feature_importances_'):
        importance = pd.DataFrame({
            'feature': X_test.columns,
            'importance': model.feature_importances_
        }).sort_values('importance', ascending=False)

        print("\nTop 10 Features:")
        print(importance.head(10))

    return {
        'auc': auc,
        'confusion_matrix': cm,
        'predictions': y_pred
    }

╔════════════════════════════════════════════════════════════╗
║                   CODE QUALITY                             ║
╚════════════════════════════════════════════════════════════╝

✅ Write Clean Code:
─────────────────────────────────────────────────────────────
• Use meaningful variable names
• Write functions (DRY principle)
• Add docstrings
• Use type hints
• Follow PEP 8
• Use linters (pylint, flake8)
• Format code (black)
• Write unit tests
• Use version control (git)

Example Clean Code:
─────────────────────────────────────────────────────────────
from typing import Tuple
import numpy as np
from sklearn.base import BaseEstimator

def train_and_evaluate(
    model: BaseEstimator,
    X_train: np.ndarray,
    y_train: np.ndarray,
    X_test: np.ndarray,
    y_test: np.ndarray
) -> Tuple[BaseEstimator, float]:
    """
    Train model and evaluate on test set.

    Parameters
    ----------
    model : BaseEstimator
        Scikit-learn compatible model
    X_train : np.ndarray
        Training features
    y_train : np.ndarray
        Training labels
    X_test : np.ndarray
        Test features
    y_test : np.ndarray
        Test labels

    Returns
    -------
    Tuple[BaseEstimator, float]
        Trained model and test accuracy
    """
    # Train
    model.fit(X_train, y_train)

    # Evaluate
    accuracy = model.score(X_test, y_test)

    return model, accuracy

╔════════════════════════════════════════════════════════════╗
║                   REPRODUCIBILITY                          ║
╚════════════════════════════════════════════════════════════╝

Ensure Reproducibility:
─────────────────────────────────────────────────────────────
1. Set random seeds
2. Version dependencies (requirements.txt)
3. Document environment
4. Version data
5. Track experiments
6. Save configurations
7. Document hardware used

Example:
─────────────────────────────────────────────────────────────
import random
import numpy as np
import torch

def set_seeds(seed=42):
    """Set seeds for reproducibility."""
    random.seed(seed)
    np.random.seed(seed)
    torch.manual_seed(seed)
    if torch.cuda.is_available():
        torch.cuda.manual_seed_all(seed)

# requirements.txt with versions
"""
scikit-learn==1.3.0
xgboost==2.0.0
numpy==1.24.3
pandas==2.0.3
torch==2.0.1
"""

╔════════════════════════════════════════════════════════════╗
║                   SECURITY                                 ║
╚════════════════════════════════════════════════════════════╝

Security Best Practices:
─────────────────────────────────────────────────────────────
✅ Sanitize user inputs
✅ Validate data types and ranges
✅ Use environment variables for secrets
✅ Don't commit sensitive data
✅ Implement rate limiting
✅ Log access and errors
✅ Use HTTPS for API
✅ Validate model outputs
✅ Monitor for adversarial inputs
✅ Regular security audits

Example Input Validation:
─────────────────────────────────────────────────────────────
def validate_input(features, expected_shape):
    """Validate input features."""
    if not isinstance(features, np.ndarray):
        raise ValueError("Features must be numpy array")

    if features.shape[1] != expected_shape:
        raise ValueError(f"Expected {expected_shape} features")

    if np.isnan(features).any():
        raise ValueError("Features contain NaN")

    if np.isinf(features).any():
        raise ValueError("Features contain infinity")

    return True

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔧 Real-World Projects

</div>

### End-to-End ML Projects 💼

```python
# ═══════════════════════════════════════════
# PROJECT 1: IMAGE CLASSIFICATION PIPELINE
# ═══════════════════════════════════════════

"""
Complete Image Classification Project
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Goal: Build production-ready image classifier
Dataset: CIFAR-10 (60K images, 10 classes)
Framework: PyTorch
"""

import torch
import torch.nn as nn
import torchvision
import torchvision.transforms as transforms
from torch.utils.data import DataLoader
import pytorch_lightning as pl

# 1. Data Module
class CIFAR10DataModule(pl.LightningDataModule):
    def __init__(self, batch_size=128):
        super().__init__()
        self.batch_size = batch_size
        self.transform_train = transforms.Compose([
            transforms.RandomCrop(32, padding=4),
            transforms.RandomHorizontalFlip(),
            transforms.ToTensor(),
            transforms.Normalize((0.5, 0.5, 0.5), (0.5, 0.5, 0.5))
        ])
        self.transform_test = transforms.Compose([
            transforms.ToTensor(),
            transforms.Normalize((0.5, 0.5, 0.5), (0.5, 0.5, 0.5))
        ])

    def setup(self, stage=None):
        self.train_dataset = torchvision.datasets.CIFAR10(
            root='./data', train=True, download=True,
            transform=self.transform_train
        )
        self.test_dataset = torchvision.datasets.CIFAR10(
            root='./data', train=False, download=True,
            transform=self.transform_test
        )

    def train_dataloader(self):
        return DataLoader(self.train_dataset, batch_size=self.batch_size,
                         shuffle=True, num_workers=4)

    def val_dataloader(self):
        return DataLoader(self.test_dataset, batch_size=self.batch_size,
                         num_workers=4)

# 2. Model
class ResNetClassifier(pl.LightningModule):
    def __init__(self, num_classes=10):
        super().__init__()
        self.model = torchvision.models.resnet18(pretrained=True)
        self.model.fc = nn.Linear(self.model.fc.in_features, num_classes)
        self.criterion = nn.CrossEntropyLoss()

    def forward(self, x):
        return self.model(x)

    def training_step(self, batch, batch_idx):
        x, y = batch
        logits = self(x)
        loss = self.criterion(logits, y)
        acc = (logits.argmax(dim=1) == y).float().mean()

        self.log('train_loss', loss)
        self.log('train_acc', acc)
        return loss

    def validation_step(self, batch, batch_idx):
        x, y = batch
        logits = self(x)
        loss = self.criterion(logits, y)
        acc = (logits.argmax(dim=1) == y).float().mean()

        self.log('val_loss', loss)
        self.log('val_acc', acc)

    def configure_optimizers(self):
        optimizer = torch.optim.Adam(self.parameters(), lr=0.001)
        scheduler = torch.optim.lr_scheduler.ReduceLROnPlateau(
            optimizer, patience=3
        )
        return {
            'optimizer': optimizer,
            'lr_scheduler': scheduler,
            'monitor': 'val_loss'
        }

# 3. Training
data_module = CIFAR10DataModule(batch_size=128)
model = ResNetClassifier(num_classes=10)

trainer = pl.Trainer(
    max_epochs=10,
    accelerator='auto',
    callbacks=[
        pl.callbacks.EarlyStopping(monitor='val_loss', patience=5),
        pl.callbacks.ModelCheckpoint(monitor='val_acc', mode='max')
    ]
)

# trainer.fit(model, data_module)

print("✅ Image Classification Project Template Ready")

# ═══════════════════════════════════════════
# PROJECT 2: CUSTOMER CHURN PREDICTION
# ═══════════════════════════════════════════

"""
Tabular Data Classification
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Goal: Predict customer churn
Framework: XGBoost
"""

import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import LabelEncoder
import xgboost as xgb

class ChurnPredictor:
    def __init__(self):
        self.model = None
        self.encoders = {}
        self.feature_names = None

    def preprocess(self, df, fit=True):
        # Handle categorical features
        categorical_cols = df.select_dtypes(include='object').columns

        for col in categorical_cols:
            if fit:
                self.encoders[col] = LabelEncoder()
                df[col] = self.encoders[col].fit_transform(df[col])
            else:
                df[col] = self.encoders[col].transform(df[col])

        return df

    def train(self, X_train, y_train, X_val, y_val):
        # Preprocess
        X_train = self.preprocess(X_train, fit=True)
        X_val = self.preprocess(X_val, fit=False)

        self.feature_names = X_train.columns.tolist()

        # Train XGBoost
        dtrain = xgb.DMatrix(X_train, label=y_train)
        dval = xgb.DMatrix(X_val, label=y_val)

        params = {
            'objective': 'binary:logistic',
            'max_depth': 5,
            'learning_rate': 0.1,
            'eval_metric': 'auc'
        }

        evals = [(dtrain, 'train'), (dval, 'val')]

        self.model = xgb.train(
            params,
            dtrain,
            num_boost_round=100,
            evals=evals,
            early_stopping_rounds=10,
            verbose_eval=False
        )

        return self

    def predict(self, X):
        X = self.preprocess(X, fit=False)
        dtest = xgb.DMatrix(X)
        return self.model.predict(dtest)

    def get_feature_importance(self):
        importance = self.model.get_score(importance_type='gain')
        return pd.DataFrame({
            'feature': importance.keys(),
            'importance': importance.values()
        }).sort_values('importance', ascending=False)

print("✅ Churn Prediction Project Template Ready")

# ═══════════════════════════════════════════
# PROJECT 3: NLP SENTIMENT ANALYSIS
# ═══════════════════════════════════════════

"""
Text Classification with Transformers
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Goal: Sentiment analysis
Framework: Hugging Face Transformers
"""

"""
from transformers import (AutoTokenizer, AutoModelForSequenceClassification,
                         Trainer, TrainingArguments)
from datasets import load_dataset
import numpy as np

# 1. Load Data
dataset = load_dataset('imdb')

# 2. Load Pre-trained Model
model_name = 'distilbert-base-uncased'
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForSequenceClassification.from_pretrained(
    model_name, num_labels=2
)

# 3. Tokenize
def tokenize_function(examples):
    return tokenizer(examples['text'], padding='max_length',
                    truncation=True, max_length=512)

tokenized_datasets = dataset.map(tokenize_function, batched=True)

# 4. Training Arguments
training_args = TrainingArguments(
    output_dir='./results',
    num_train_epochs=3,
    per_device_train_batch_size=16,
    per_device_eval_batch_size=64,
    warmup_steps=500,
    weight_decay=0.01,
    logging_dir='./logs',
    evaluation_strategy='epoch'
)

# 5. Trainer
trainer = Trainer(
    model=model,
    args=training_args,
    train_dataset=tokenized_datasets['train'],
    eval_dataset=tokenized_datasets['test']
)

# 6. Train
trainer.train()

# 7. Evaluate
results = trainer.evaluate()
print(results)
"""

print("✅ NLP Sentiment Analysis Project Template Ready")

print("\n" + "="*60)
print("All project templates ready for implementation!")
print("="*60)
```

---

<div align="center">

## 📚 Resources & Learning

</div>

### Continue Your ML Journey 🚀

```
📘 Official Documentation
   • Scikit-learn: https://scikit-learn.org/
   • TensorFlow: https://www.tensorflow.org/
   • PyTorch: https://pytorch.org/
   • XGBoost: https://xgboost.readthedocs.io/
   • LightGBM: https://lightgbm.readthedocs.io/
   • CatBoost: https://catboost.ai/

📗 Books
   • Hands-On Machine Learning (Aurélien Géron)
   • Deep Learning (Goodfellow, Bengio, Courville)
   • Pattern Recognition and Machine Learning (Bishop)
   • The Hundred-Page Machine Learning Book (Andriy Burkov)

📙 Online Courses
   • FastAI Practical Deep Learning
   • Coursera ML Specialization (Andrew Ng)
   • Deep Learning Specialization
   • Full Stack Deep Learning

🎥 YouTube Channels
   • Yannic Kilcher (Paper reviews)
   • Two Minute Papers
   • Sentdex
   • StatQuest

💻 Practice Platforms
   • Kaggle: https://www.kaggle.com/
   • DrivenData: https://www.drivendata.org/
   • Papers with Code: https://paperswithcode.com/

🛠️ Tools
   • MLflow: Experiment tracking
   • Weights & Biases: Experiment tracking
   • DVC: Data version control
   • Optuna: Hyperparameter optimization
   • SHAP: Model interpretability

💬 Communities
   • r/MachineLearning
   • r/learnmachinelearning
   • AI Alignment Forum
   • Papers with Code
   • Discord ML communities
```

---

<div align="center">

## 🎯 Summary

</div>

### Key Takeaways 💡

```bash
╔════════════════════════════════════════════════════════════╗
║                   REMEMBER                                 ║
╚════════════════════════════════════════════════════════════╝

1. Choose the Right Framework
   • Scikit-learn: Classical ML, tabular data
   • XGBoost/LightGBM: Structured data, competitions
   • TensorFlow: Production, deployment
   • PyTorch: Research, flexibility

2. Start Simple
   • Baseline model first
   • Add complexity gradually
   • Evaluate thoroughly
   • Document everything

3. Focus on Data
   • Quality > Quantity
   • Feature engineering matters
   • Validate continuously
   • Monitor drift

4. Best Practices
   • Version control everything
   • Write clean code
   • Test your code
   • Track experiments
   • Reproduce results

5. Production Readiness
   • API design
   • Monitoring
   • Logging
   • Error handling
   • Security

"The best model is the one that solves the business problem,
not the one with the highest accuracy." ✨

═══════════════════════════════════════════════════════════
```

---

<div align="center">

**Built with 🤖 by MrDib, for ML practitioners**

_Remember: "In ML, the model is 10%, the data is 90%"_ 📊

**Happy Machine Learning!** 🚀
