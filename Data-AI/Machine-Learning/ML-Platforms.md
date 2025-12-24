<div align="center">

# 🚀 ML Platforms - Complete Guide

![ML Platforms](https://img.shields.io/badge/ML-Platforms-purple?style=for-the-badge&logo=databricks)
![Cloud](https://img.shields.io/badge/Cloud-ML-blue?style=for-the-badge&logo=amazonaws)
![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=for-the-badge)

### _From experimentation to production - streamline your ML workflow_ ⚡

**Build, deploy, and manage ML at scale** 🌟

</div>

---

## 📚 Table of Contents

- [🎯 Platform Overview](#-platform-overview)
- [☁️ Cloud ML Platforms](#️-cloud-ml-platforms)
- [🤖 AutoML Platforms](#-automl-platforms)
- [🔄 MLOps Platforms](#-mlops-platforms)
- [📊 Experiment Tracking](#-experiment-tracking)
- [🎯 Feature Stores](#-feature-stores)
- [🚀 Model Serving](#-model-serving)
- [🏢 End-to-End Platforms](#-end-to-end-platforms)
- [📊 Platform Comparison](#-platform-comparison)
- [💡 Best Practices](#-best-practices)
- [🔧 Implementation Guide](#-implementation-guide)

---

<div align="center">

## 🎯 Platform Overview

</div>

### Understanding ML Platforms 📖

```bash
# ═══════════════════════════════════════════
# WHAT ARE ML PLATFORMS?
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ML PLATFORM DEFINITION                   ║
╚════════════════════════════════════════════════════════════╝

ML Platforms: Integrated environments for end-to-end ML lifecycle
─────────────────────────────────────────────────────────────
• Streamline ML workflows
• Manage experiments
• Version models and data
• Deploy at scale
• Monitor performance
• Collaborate across teams

The ML Lifecycle:
─────────────────────────────────────────────────────────────

┌─────────────────────────────────────────────────────────┐
│  1. DATA                                                │
│     ├─ Collection                                       │
│     ├─ Labeling                                        │
│     ├─ Versioning                                      │
│     └─ Storage                                         │
│                                                         │
│  2. EXPERIMENTATION                                     │
│     ├─ Feature engineering                             │
│     ├─ Model training                                  │
│     ├─ Hyperparameter tuning                          │
│     └─ Experiment tracking                            │
│                                                         │
│  3. DEPLOYMENT                                          │
│     ├─ Model serving                                   │
│     ├─ A/B testing                                     │
│     ├─ Canary releases                                │
│     └─ Monitoring                                      │
│                                                         │
│  4. MONITORING & MAINTENANCE                            │
│     ├─ Performance tracking                            │
│     ├─ Data drift detection                           │
│     ├─ Model retraining                               │
│     └─ Feedback loops                                 │
└─────────────────────────────────────────────────────────┘

╔════════════════════════════════════════════════════════════╗
║                   PLATFORM CATEGORIES                      ║
╚════════════════════════════════════════════════════════════╝

1. Cloud ML Platforms
─────────────────────────────────────────────────────────────
   • AWS SageMaker
   • Google Vertex AI
   • Azure Machine Learning
   • IBM Watson Studio

2. AutoML Platforms
─────────────────────────────────────────────────────────────
   • H2O.ai
   • DataRobot
   • Google AutoML
   • AutoGluon

3. MLOps Platforms
─────────────────────────────────────────────────────────────
   • MLflow
   • Kubeflow
   • Seldon Core
   • BentoML

4. Experiment Tracking
─────────────────────────────────────────────────────────────
   • Weights & Biases
   • Neptune.ai
   • Comet.ml
   • MLflow Tracking

5. Feature Stores
─────────────────────────────────────────────────────────────
   • Feast
   • Tecton
   • Hopsworks
   • AWS Feature Store

6. Model Serving
─────────────────────────────────────────────────────────────
   • TensorFlow Serving
   • TorchServe
   • NVIDIA Triton
   • Seldon Core

7. End-to-End Platforms
─────────────────────────────────────────────────────────────
   • Databricks
   • Dataiku
   • Domino Data Lab
   • Alteryx

╔════════════════════════════════════════════════════════════╗
║                   WHY USE ML PLATFORMS?                    ║
╚════════════════════════════════════════════════════════════╝

Benefits:
─────────────────────────────────────────────────────────────
✅ Faster time to production
✅ Standardized workflows
✅ Collaboration tools
✅ Version control (models, data, code)
✅ Scalable infrastructure
✅ Cost optimization
✅ Monitoring & observability
✅ Compliance & governance
✅ Reproducibility
✅ Team productivity

Challenges Without Platforms:
─────────────────────────────────────────────────────────────
❌ Manual setup & configuration
❌ Inconsistent environments
❌ Lost experiments
❌ Deployment complexity
❌ Monitoring gaps
❌ Scaling difficulties
❌ Team silos
❌ Version control issues

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## ☁️ Cloud ML Platforms

</div>

### Enterprise-Grade ML in the Cloud 🌩️

```python
# ═══════════════════════════════════════════
# AWS SAGEMAKER
# ═══════════════════════════════════════════

"""
AWS SageMaker: Fully managed ML service
- Notebooks (Jupyter)
- Training (distributed)
- Hyperparameter tuning
- Model deployment
- Monitoring
- Feature Store
- Pipelines
"""

import boto3
import sagemaker
from sagemaker import get_execution_role
from sagemaker.sklearn import SKLearn
from sagemaker.tensorflow import TensorFlow
import pandas as pd

print("="*60)
print("AWS SAGEMAKER")
print("="*60)

# Initialize
role = get_execution_role()
sagemaker_session = sagemaker.Session()
bucket = sagemaker_session.default_bucket()

print(f"SageMaker Role: {role}")
print(f"Default Bucket: {bucket}")

# ─────────────────────────────────────────────
# 1. TRAINING WITH SAGEMAKER
# ─────────────────────────────────────────────

"""
# train.py (training script)
import argparse
import os
import pandas as pd
from sklearn.ensemble import RandomForestClassifier
import joblib

if __name__ == '__main__':
    parser = argparse.ArgumentParser()

    # Hyperparameters
    parser.add_argument('--n-estimators', type=int, default=100)
    parser.add_argument('--max-depth', type=int, default=5)

    # Data directories
    parser.add_argument('--train', type=str, default=os.environ.get('SM_CHANNEL_TRAIN'))
    parser.add_argument('--model-dir', type=str, default=os.environ.get('SM_MODEL_DIR'))

    args = parser.parse_args()

    # Load data
    train_data = pd.read_csv(f'{args.train}/train.csv')
    X_train = train_data.drop('target', axis=1)
    y_train = train_data['target']

    # Train model
    model = RandomForestClassifier(
        n_estimators=args.n_estimators,
        max_depth=args.max_depth
    )
    model.fit(X_train, y_train)

    # Save model
    joblib.dump(model, f'{args.model_dir}/model.joblib')
"""

# Create estimator
sklearn_estimator = SKLearn(
    entry_point='train.py',
    role=role,
    instance_type='ml.m5.xlarge',
    framework_version='1.0-1',
    hyperparameters={
        'n-estimators': 100,
        'max-depth': 5
    }
)

# Training (example - would upload data first)
# sklearn_estimator.fit({'train': 's3://bucket/train-data'})

print("\n✅ SageMaker Training Example")

# ─────────────────────────────────────────────
# 2. HYPERPARAMETER TUNING
# ─────────────────────────────────────────────

from sagemaker.tuner import (HyperparameterTuner, IntegerParameter,
                             ContinuousParameter)

hyperparameter_ranges = {
    'n-estimators': IntegerParameter(50, 300),
    'max-depth': IntegerParameter(3, 15)
}

tuner = HyperparameterTuner(
    sklearn_estimator,
    objective_metric_name='accuracy',
    hyperparameter_ranges=hyperparameter_ranges,
    max_jobs=10,
    max_parallel_jobs=2
)

# tuner.fit({'train': 's3://bucket/train-data'})

print("✅ Hyperparameter Tuning Configured")

# ─────────────────────────────────────────────
# 3. MODEL DEPLOYMENT
# ─────────────────────────────────────────────

# Deploy model
# predictor = sklearn_estimator.deploy(
#     initial_instance_count=1,
#     instance_type='ml.t2.medium'
# )

# Make predictions
# predictions = predictor.predict(test_data)

# Delete endpoint
# predictor.delete_endpoint()

print("✅ SageMaker Deployment Example")

# ─────────────────────────────────────────────
# 4. SAGEMAKER PIPELINES
# ─────────────────────────────────────────────

from sagemaker.workflow.pipeline import Pipeline
from sagemaker.workflow.steps import TrainingStep, ProcessingStep
from sagemaker.workflow.parameters import ParameterInteger

"""
# Define pipeline
n_estimators = ParameterInteger(name="NumEstimators", default_value=100)

# Processing step
processing_step = ProcessingStep(
    name="PreprocessData",
    processor=sklearn_processor,
    inputs=[...],
    outputs=[...],
    code="preprocess.py"
)

# Training step
training_step = TrainingStep(
    name="TrainModel",
    estimator=sklearn_estimator,
    inputs={'train': processing_step.properties.ProcessingOutputConfig.Outputs['train'].S3Output.S3Uri}
)

# Create pipeline
pipeline = Pipeline(
    name="MyMLPipeline",
    parameters=[n_estimators],
    steps=[processing_step, training_step]
)

# Start pipeline
pipeline.upsert(role_arn=role)
execution = pipeline.start()
"""

print("✅ SageMaker Pipelines Example")

# ═══════════════════════════════════════════
# GOOGLE VERTEX AI
# ═══════════════════════════════════════════

"""
Google Vertex AI: Unified ML platform
- AutoML
- Custom training
- Hyperparameter tuning
- Model deployment
- Feature Store
- Pipelines
- Monitoring
"""

print("\n" + "="*60)
print("GOOGLE VERTEX AI")
print("="*60)

"""
from google.cloud import aiplatform

# Initialize
aiplatform.init(
    project='my-project',
    location='us-central1'
)

# ─────────────────────────────────────────────
# 1. CUSTOM TRAINING
# ─────────────────────────────────────────────

job = aiplatform.CustomTrainingJob(
    display_name='my-training-job',
    script_path='train.py',
    container_uri='gcr.io/cloud-aiplatform/training/tf-cpu.2-8:latest',
    requirements=['pandas', 'scikit-learn'],
    model_serving_container_image_uri='gcr.io/cloud-aiplatform/prediction/tf2-cpu.2-8:latest'
)

# Run training
model = job.run(
    dataset=dataset,
    replica_count=1,
    machine_type='n1-standard-4',
    training_fraction_split=0.8,
    validation_fraction_split=0.1,
    test_fraction_split=0.1
)

# ─────────────────────────────────────────────
# 2. AUTOML
# ─────────────────────────────────────────────

dataset = aiplatform.TabularDataset.create(
    display_name='my-dataset',
    gcs_source=['gs://bucket/data.csv']
)

job = aiplatform.AutoMLTabularTrainingJob(
    display_name='automl-training',
    optimization_prediction_type='classification',
    optimization_objective='maximize-au-prc'
)

model = job.run(
    dataset=dataset,
    target_column='target',
    training_fraction_split=0.8,
    validation_fraction_split=0.1,
    test_fraction_split=0.1,
    budget_milli_node_hours=1000,
    model_display_name='automl-model'
)

# ─────────────────────────────────────────────
# 3. MODEL DEPLOYMENT
# ─────────────────────────────────────────────

endpoint = model.deploy(
    deployed_model_display_name='my-model',
    machine_type='n1-standard-4',
    min_replica_count=1,
    max_replica_count=3
)

# Make predictions
predictions = endpoint.predict(instances=[[1, 2, 3, 4]])

# ─────────────────────────────────────────────
# 4. VERTEX AI PIPELINES
# ─────────────────────────────────────────────

from kfp.v2 import dsl
from kfp.v2.dsl import component

@component
def preprocess_data(input_path: str) -> str:
    # Preprocessing logic
    return output_path

@component
def train_model(data_path: str) -> str:
    # Training logic
    return model_path

@dsl.pipeline(name='my-pipeline')
def ml_pipeline():
    preprocess_task = preprocess_data(input_path='gs://bucket/data.csv')
    train_task = train_model(data_path=preprocess_task.output)

# Compile and run
from kfp.v2 import compiler
compiler.Compiler().compile(
    pipeline_func=ml_pipeline,
    package_path='pipeline.json'
)

job = aiplatform.PipelineJob(
    display_name='my-pipeline-job',
    template_path='pipeline.json'
)
job.run()
"""

print("✅ Vertex AI Examples")

# ═══════════════════════════════════════════
# AZURE MACHINE LEARNING
# ═══════════════════════════════════════════

"""
Azure ML: Microsoft's ML platform
- Notebooks
- Automated ML
- Designer (drag-and-drop)
- Training (compute clusters)
- Deployment
- Monitoring
- MLOps
"""

print("\n" + "="*60)
print("AZURE MACHINE LEARNING")
print("="*60)

"""
from azureml.core import Workspace, Experiment, Environment
from azureml.core.compute import ComputeTarget, AmlCompute
from azureml.train.sklearn import SKLearn

# Connect to workspace
ws = Workspace.from_config()

# ─────────────────────────────────────────────
# 1. CREATE COMPUTE CLUSTER
# ─────────────────────────────────────────────

compute_config = AmlCompute.provisioning_configuration(
    vm_size='STANDARD_D2_V2',
    max_nodes=4,
    idle_seconds_before_scaledown=300
)

compute_target = ComputeTarget.create(
    ws, 'cpu-cluster', compute_config
)
compute_target.wait_for_completion(show_output=True)

# ─────────────────────────────────────────────
# 2. TRAINING
# ─────────────────────────────────────────────

experiment = Experiment(workspace=ws, name='my-experiment')

estimator = SKLearn(
    source_directory='./src',
    entry_script='train.py',
    compute_target=compute_target,
    pip_packages=['pandas', 'scikit-learn']
)

run = experiment.submit(estimator)
run.wait_for_completion(show_output=True)

# ─────────────────────────────────────────────
# 3. AUTOMATED ML
# ─────────────────────────────────────────────

from azureml.train.automl import AutoMLConfig

automl_config = AutoMLConfig(
    task='classification',
    primary_metric='AUC_weighted',
    training_data=dataset,
    label_column_name='target',
    n_cross_validations=5,
    enable_early_stopping=True,
    experiment_timeout_hours=1,
    max_concurrent_iterations=4
)

automl_run = experiment.submit(automl_config, show_output=True)
best_run, fitted_model = automl_run.get_output()

# ─────────────────────────────────────────────
# 4. MODEL DEPLOYMENT
# ─────────────────────────────────────────────

from azureml.core.model import InferenceConfig, Model
from azureml.core.webservice import AciWebservice

# Register model
model = run.register_model(
    model_name='sklearn-model',
    model_path='outputs/model.pkl'
)

# Inference configuration
inference_config = InferenceConfig(
    entry_script='score.py',
    environment=environment
)

# Deployment configuration
deployment_config = AciWebservice.deploy_configuration(
    cpu_cores=1,
    memory_gb=1
)

# Deploy
service = Model.deploy(
    workspace=ws,
    name='my-service',
    models=[model],
    inference_config=inference_config,
    deployment_config=deployment_config
)

service.wait_for_deployment(show_output=True)

# Test service
import json
test_data = json.dumps({'data': [[1, 2, 3, 4]]})
prediction = service.run(test_data)
"""

print("✅ Azure ML Examples")

print("\n" + "="*60)
print("Cloud ML Platforms Overview Complete")
print("="*60)
```

---

<div align="center">

## 🤖 AutoML Platforms

</div>

### Automated Machine Learning 🔮

```python
# ═══════════════════════════════════════════
# AUTOML PLATFORMS
# ═══════════════════════════════════════════

"""
AutoML: Automated machine learning
- Automated feature engineering
- Model selection
- Hyperparameter tuning
- Ensemble methods
- No-code/low-code
"""

print("="*60)
print("AUTOML PLATFORMS")
print("="*60)

# ═══════════════════════════════════════════
# H2O.AI
# ═══════════════════════════════════════════

"""
H2O.ai: Open-source AutoML platform
- H2O AutoML
- Driverless AI (commercial)
- Model interpretability
- Production deployment
"""

print("\n" + "="*60)
print("H2O.AI")
print("="*60)

# Install: pip install h2o

import h2o
from h2o.automl import H2OAutoML
import pandas as pd

# Initialize H2O
# h2o.init()

"""
# Load data
df = pd.read_csv('data.csv')
h2o_df = h2o.H2OFrame(df)

# Split data
train, test = h2o_df.split_frame(ratios=[0.8])

# Define features and target
x = h2o_df.columns
x.remove('target')
y = 'target'

# Run AutoML
aml = H2OAutoML(
    max_models=20,
    max_runtime_secs=3600,  # 1 hour
    seed=42
)

aml.train(x=x, y=y, training_frame=train)

# View leaderboard
lb = aml.leaderboard
print(lb.head())

# Best model
best_model = aml.leader

# Predictions
predictions = best_model.predict(test)

# Model explanation
best_model.explain(test)

# Save model
h2o.save_model(best_model, path='models/')

# Load model
loaded_model = h2o.load_model('models/best_model')
"""

print("✅ H2O AutoML Example")

# ═══════════════════════════════════════════
# AUTOGLUON
# ═══════════════════════════════════════════

"""
AutoGluon: AutoML for deep learning and tabular data
- Tabular, text, image
- Stacking/ensembling
- Fast and accurate
"""

print("\n" + "="*60)
print("AUTOGLUON")
print("="*60)

# Install: pip install autogluon

from autogluon.tabular import TabularDataset, TabularPredictor
import pandas as pd

"""
# Load data
train_data = TabularDataset('train.csv')
test_data = TabularDataset('test.csv')

# Define target
label = 'target'

# Train AutoML
predictor = TabularPredictor(
    label=label,
    eval_metric='accuracy',
    path='autogluon_models'
).fit(
    train_data=train_data,
    time_limit=3600,  # 1 hour
    presets='best_quality'  # or 'medium_quality', 'optimize_for_deployment'
)

# Leaderboard
leaderboard = predictor.leaderboard(test_data, silent=True)
print(leaderboard)

# Predictions
predictions = predictor.predict(test_data)
probabilities = predictor.predict_proba(test_data)

# Feature importance
feature_importance = predictor.feature_importance(test_data)
print(feature_importance)

# Evaluate
performance = predictor.evaluate(test_data)
print(performance)
"""

print("✅ AutoGluon Example")

# ═══════════════════════════════════════════
# PYCARET
# ═══════════════════════════════════════════

"""
PyCaret: Low-code ML library
- Classification, regression, clustering
- Model comparison
- Hyperparameter tuning
- Model deployment
"""

print("\n" + "="*60)
print("PYCARET")
print("="*60)

# Install: pip install pycaret

from pycaret.classification import *
import pandas as pd

"""
# Load data
data = pd.read_csv('data.csv')

# Setup
clf = setup(
    data=data,
    target='target',
    session_id=42,
    log_experiment=True,
    experiment_name='my_experiment'
)

# Compare models
best_model = compare_models()

# Create model
rf = create_model('rf')

# Tune model
tuned_rf = tune_model(rf)

# Ensemble model
bagged_rf = ensemble_model(tuned_rf, method='Bagging')

# Plot model
plot_model(tuned_rf, plot='auc')
plot_model(tuned_rf, plot='confusion_matrix')
plot_model(tuned_rf, plot='feature')

# Predict
predictions = predict_model(tuned_rf, data=test_data)

# Save model
save_model(tuned_rf, 'my_model')

# Load model
loaded_model = load_model('my_model')

# Deploy (creates API)
deploy_model(tuned_rf, model_name='my_api', platform='aws')
"""

print("✅ PyCaret Example")

# ═══════════════════════════════════════════
# TPOT
# ═══════════════════════════════════════════

"""
TPOT: Tree-based Pipeline Optimization Tool
- Genetic programming
- Pipeline optimization
- Scikit-learn compatible
"""

print("\n" + "="*60)
print("TPOT")
print("="*60)

# Install: pip install tpot

from tpot import TPOTClassifier
from sklearn.model_selection import train_test_split
import pandas as pd

"""
# Load data
df = pd.read_csv('data.csv')
X = df.drop('target', axis=1)
y = df['target']

# Split data
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

# Run TPOT
tpot = TPOTClassifier(
    generations=5,
    population_size=50,
    verbosity=2,
    random_state=42,
    n_jobs=-1,
    scoring='accuracy'
)

tpot.fit(X_train, y_train)

# Best pipeline
print(tpot.fitted_pipeline_)

# Evaluate
accuracy = tpot.score(X_test, y_test)
print(f'Accuracy: {accuracy:.4f}')

# Export pipeline
tpot.export('tpot_pipeline.py')

# The exported pipeline can be used like:
# from tpot_pipeline import *
# pipeline.fit(X_train, y_train)
# predictions = pipeline.predict(X_test)
"""

print("✅ TPOT Example")

print("\n" + "="*60)
print("AutoML Platforms Overview Complete")
print("="*60)
```

---

<div align="center">

## 🔄 MLOps Platforms

</div>

### End-to-End ML Operations 🔧

```python
# ═══════════════════════════════════════════
# MLOPS PLATFORMS
# ═══════════════════════════════════════════

"""
MLOps: Machine Learning Operations
- Versioning (models, data, code)
- Reproducibility
- CI/CD for ML
- Monitoring
- Collaboration
"""

print("="*60)
print("MLOPS PLATFORMS")
print("="*60)

# ═══════════════════════════════════════════
# MLFLOW
# ═══════════════════════════════════════════

"""
MLflow: Open-source ML lifecycle platform
- Tracking: Log experiments
- Projects: Package code
- Models: Package and deploy
- Registry: Manage models
"""

print("\n" + "="*60)
print("MLFLOW")
print("="*60)

# Install: pip install mlflow

import mlflow
import mlflow.sklearn
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score
import numpy as np

# ─────────────────────────────────────────────
# 1. EXPERIMENT TRACKING
# ─────────────────────────────────────────────

# Set experiment
mlflow.set_experiment("my-experiment")

# Start run
with mlflow.start_run():
    # Log parameters
    params = {
        'n_estimators': 100,
        'max_depth': 10,
        'random_state': 42
    }
    mlflow.log_params(params)

    # Train model
    model = RandomForestClassifier(**params)
    # model.fit(X_train, y_train)

    # Log metrics
    # accuracy = accuracy_score(y_test, model.predict(X_test))
    # mlflow.log_metric('accuracy', accuracy)

    # Log model
    # mlflow.sklearn.log_model(model, 'model')

    # Log artifacts
    # mlflow.log_artifact('plots/confusion_matrix.png')

    print("✅ Experiment tracked")

# ─────────────────────────────────────────────
# 2. MODEL REGISTRY
# ─────────────────────────────────────────────

"""
# Register model
model_uri = f'runs:/{run_id}/model'
mv = mlflow.register_model(model_uri, 'MyModel')

# Transition model stage
from mlflow.tracking import MlflowClient
client = MlflowClient()

client.transition_model_version_stage(
    name='MyModel',
    version=1,
    stage='Production'
)

# Load model
model = mlflow.pyfunc.load_model('models:/MyModel/Production')
predictions = model.predict(X_test)
"""

print("✅ Model Registry Example")

# ─────────────────────────────────────────────
# 3. MLFLOW PROJECTS
# ─────────────────────────────────────────────

"""
# MLproject file
name: my-ml-project

conda_env: conda.yaml

entry_points:
  main:
    parameters:
      n_estimators: {type: int, default: 100}
      max_depth: {type: int, default: 5}
    command: "python train.py --n-estimators {n_estimators} --max-depth {max_depth}"

# Run project
mlflow run . -P n_estimators=200 -P max_depth=10

# Run from Git
mlflow run https://github.com/user/repo -P param=value
"""

print("✅ MLflow Projects Example")

# ─────────────────────────────────────────────
# 4. MODEL SERVING
# ─────────────────────────────────────────────

"""
# Serve model locally
mlflow models serve -m models:/MyModel/Production -p 5000

# Docker deployment
mlflow models build-docker -m models:/MyModel/Production -n my-model

# Cloud deployment (AWS SageMaker)
mlflow deployments create -t sagemaker -m models:/MyModel/Production \
    --name my-model --config config.yaml
"""

print("✅ MLflow Serving Example")

# ═══════════════════════════════════════════
# KUBEFLOW
# ═══════════════════════════════════════════

"""
Kubeflow: ML toolkit for Kubernetes
- Pipelines
- Training operators
- Serving (KFServing)
- Experiments
- Notebooks
"""

print("\n" + "="*60)
print("KUBEFLOW")
print("="*60)

"""
# Install: pip install kfp

import kfp
from kfp import dsl

# Define component
@dsl.component
def preprocess_data(input_path: str) -> str:
    # Implementation
    return output_path

@dsl.component
def train_model(data_path: str, n_estimators: int) -> str:
    # Implementation
    return model_path

@dsl.component
def evaluate_model(model_path: str, test_data: str) -> float:
    # Implementation
    return accuracy

# Define pipeline
@dsl.pipeline(
    name='ML Pipeline',
    description='End-to-end ML pipeline'
)
def ml_pipeline(input_data: str, n_estimators: int = 100):
    preprocess_task = preprocess_data(input_path=input_data)
    train_task = train_model(
        data_path=preprocess_task.output,
        n_estimators=n_estimators
    )
    evaluate_task = evaluate_model(
        model_path=train_task.output,
        test_data=preprocess_task.output
    )

# Compile pipeline
kfp.compiler.Compiler().compile(
    pipeline_func=ml_pipeline,
    package_path='pipeline.yaml'
)

# Run pipeline
client = kfp.Client(host='http://kubeflow-pipelines:8888')
run = client.create_run_from_pipeline_func(
    ml_pipeline,
    arguments={'input_data': 's3://bucket/data', 'n_estimators': 100}
)
"""

print("✅ Kubeflow Pipelines Example")

# ═══════════════════════════════════════════
# BENTOML
# ═══════════════════════════════════════════

"""
BentoML: Model serving made easy
- Package models
- API creation
- Docker containers
- Cloud deployment
"""

print("\n" + "="*60)
print("BENTOML")
print("="*60)

# Install: pip install bentoml

import bentoml
from bentoml.io import NumpyNdarray
import numpy as np

"""
# Save model
bentoml.sklearn.save_model(
    'my_model',
    model,
    signatures={'predict': {'batchable': True}}
)

# Create service (service.py)
import bentoml
from bentoml.io import NumpyNdarray

model_runner = bentoml.sklearn.get('my_model:latest').to_runner()
svc = bentoml.Service('classifier', runners=[model_runner])

@svc.api(input=NumpyNdarray(), output=NumpyNdarray())
def predict(input_array):
    result = model_runner.predict.run(input_array)
    return result

# Serve locally
# bentoml serve service:svc

# Build container
# bentoml containerize classifier:latest

# Deploy to cloud
# bentoml deploy classifier:latest --platform aws_lambda
"""

print("✅ BentoML Example")

print("\n" + "="*60)
print("MLOps Platforms Overview Complete")
print("="*60)
```

---

<div align="center">

## 📊 Experiment Tracking

</div>

### Track, Compare, and Reproduce Experiments 📈

```python
# ═══════════════════════════════════════════
# EXPERIMENT TRACKING PLATFORMS
# ═══════════════════════════════════════════

"""
Experiment Tracking: Record and compare ML experiments
- Hyperparameters
- Metrics
- Artifacts
- Code versions
- Collaboration
"""

print("="*60)
print("EXPERIMENT TRACKING")
print("="*60)

# ═══════════════════════════════════════════
# WEIGHTS & BIASES (WANDB)
# ═══════════════════════════════════════════

"""
Weights & Biases: Experiment tracking and visualization
- Real-time metrics
- Hyperparameter tuning
- Model versioning
- Collaboration
- Reports
"""

print("\n" + "="*60)
print("WEIGHTS & BIASES")
print("="*60)

# Install: pip install wandb

import wandb
import numpy as np
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split

"""
# Initialize
wandb.init(
    project='my-project',
    config={
        'n_estimators': 100,
        'max_depth': 10,
        'learning_rate': 0.01
    }
)

# Access config
config = wandb.config

# Train model
model = RandomForestClassifier(
    n_estimators=config.n_estimators,
    max_depth=config.max_depth
)
model.fit(X_train, y_train)

# Log metrics
for epoch in range(10):
    train_loss = np.random.random()
    val_loss = np.random.random()

    wandb.log({
        'epoch': epoch,
        'train_loss': train_loss,
        'val_loss': val_loss,
        'learning_rate': config.learning_rate
    })

# Log predictions
wandb.log({'predictions': wandb.Table(
    data=[[x, y] for x, y in zip(y_test, y_pred)],
    columns=['actual', 'predicted']
)})

# Log confusion matrix
wandb.sklearn.plot_confusion_matrix(y_test, y_pred, labels=['0', '1'])

# Log feature importance
wandb.sklearn.plot_feature_importances(model, feature_names)

# Save model
wandb.save('model.pkl')

# Finish run
wandb.finish()
"""

print("✅ W&B Basic Tracking")

# ─────────────────────────────────────────────
# HYPERPARAMETER SWEEPS
# ─────────────────────────────────────────────

"""
# Define sweep configuration
sweep_config = {
    'method': 'bayes',  # 'random', 'grid', 'bayes'
    'metric': {
        'name': 'val_accuracy',
        'goal': 'maximize'
    },
    'parameters': {
        'n_estimators': {
            'values': [50, 100, 200]
        },
        'max_depth': {
            'min': 3,
            'max': 15
        },
        'learning_rate': {
            'distribution': 'log_uniform_values',
            'min': 0.0001,
            'max': 0.1
        }
    }
}

# Initialize sweep
sweep_id = wandb.sweep(sweep_config, project='my-project')

# Train function
def train():
    run = wandb.init()
    config = wandb.config

    # Train model with config
    model = train_model(config)

    # Evaluate
    val_accuracy = evaluate(model)
    wandb.log({'val_accuracy': val_accuracy})

# Run sweep
wandb.agent(sweep_id, train, count=20)
"""

print("✅ W&B Hyperparameter Sweeps")

# ─────────────────────────────────────────────
# PYTORCH INTEGRATION
# ─────────────────────────────────────────────

"""
import torch
import torch.nn as nn

# Initialize
wandb.init(project='pytorch-project')

# Watch model
model = MyNeuralNetwork()
wandb.watch(model, log='all', log_freq=100)

# Training loop
for epoch in range(epochs):
    for batch in dataloader:
        # Forward pass
        outputs = model(batch)
        loss = criterion(outputs, labels)

        # Backward pass
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()

        # Log metrics
        wandb.log({'loss': loss.item()})

# Save model
torch.save(model.state_dict(), 'model.pth')
wandb.save('model.pth')
"""

print("✅ W&B with PyTorch")

# ═══════════════════════════════════════════
# NEPTUNE.AI
# ═══════════════════════════════════════════

"""
Neptune.ai: Metadata store for MLOps
- Experiment tracking
- Model registry
- Monitoring
- Team collaboration
"""

print("\n" + "="*60)
print("NEPTUNE.AI")
print("="*60)

# Install: pip install neptune-client

import neptune.new as neptune

"""
# Initialize
run = neptune.init_run(
    project='workspace/project',
    api_token='YOUR_API_TOKEN'
)

# Log parameters
params = {
    'n_estimators': 100,
    'max_depth': 10,
    'learning_rate': 0.01
}
run['parameters'] = params

# Log metrics
for epoch in range(100):
    run['train/loss'].log(train_loss)
    run['val/loss'].log(val_loss)
    run['val/accuracy'].log(accuracy)

# Log model
run['model'].upload('model.pkl')

# Log plots
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
ax.plot(history['loss'])
run['plots/loss'].upload(fig)

# Log dataset version
run['dataset/version'] = 'v1.2.0'

# Add tags
run['sys/tags'].add(['baseline', 'random-forest'])

# Stop logging
run.stop()
"""

print("✅ Neptune.ai Example")

# ═══════════════════════════════════════════
# COMET.ML
# ═══════════════════════════════════════════

"""
Comet.ml: Experiment management platform
- Tracking
- Comparison
- Monitoring
- Model registry
"""

print("\n" + "="*60)
print("COMET.ML")
print("="*60)

# Install: pip install comet-ml

from comet_ml import Experiment

"""
# Create experiment
experiment = Experiment(
    api_key='YOUR_API_KEY',
    project_name='my-project',
    workspace='my-workspace'
)

# Log parameters
experiment.log_parameters({
    'n_estimators': 100,
    'max_depth': 10,
    'learning_rate': 0.01
})

# Log metrics
for epoch in range(100):
    experiment.log_metric('loss', loss, epoch=epoch)
    experiment.log_metric('accuracy', accuracy, epoch=epoch)

# Log model
experiment.log_model('model', 'model.pkl')

# Log confusion matrix
experiment.log_confusion_matrix(y_true, y_pred)

# Log dataset
experiment.log_dataset_hash(X_train)

# End experiment
experiment.end()
"""

print("✅ Comet.ml Example")

print("\n" + "="*60)
print("Experiment Tracking Overview Complete")
print("="*60)
```

---

<div align="center">

## 🎯 Feature Stores

</div>

### Centralized Feature Management 🗄️

```python
# ═══════════════════════════════════════════
# FEATURE STORES
# ═══════════════════════════════════════════

"""
Feature Store: Centralized repository for ML features
- Consistent features (training & serving)
- Feature reusability
- Feature versioning
- Point-in-time correctness
- Real-time & batch features
"""

print("="*60)
print("FEATURE STORES")
print("="*60)

# ═══════════════════════════════════════════
# FEAST (FEATURE STORE)
# ═══════════════════════════════════════════

"""
Feast: Open-source feature store
- Online serving
- Offline retrieval
- Point-in-time joins
- Feature versioning
"""

print("\n" + "="*60)
print("FEAST")
print("="*60)

# Install: pip install feast

from feast import FeatureStore, Entity, Feature, FeatureView, FileSource
from feast.types import Float32, Int64, String
from datetime import timedelta

"""
# ─────────────────────────────────────────────
# 1. DEFINE FEATURES
# ─────────────────────────────────────────────

# Define entity (e.g., customer)
customer = Entity(
    name='customer',
    join_keys=['customer_id']
)

# Define feature view
customer_features_view = FeatureView(
    name='customer_features',
    entities=[customer],
    ttl=timedelta(days=1),
    schema=[
        Feature(name='age', dtype=Int64),
        Feature(name='income', dtype=Float32),
        Feature(name='credit_score', dtype=Int64),
        Feature(name='city', dtype=String)
    ],
    source=FileSource(
        path='data/customer_features.parquet',
        timestamp_field='event_timestamp'
    )
)

# ─────────────────────────────────────────────
# 2. REGISTER FEATURES
# ─────────────────────────────────────────────

# Initialize feature store
fs = FeatureStore(repo_path='.')

# Apply (register) features
# feast apply (from command line)

# ─────────────────────────────────────────────
# 3. OFFLINE RETRIEVAL (TRAINING)
# ─────────────────────────────────────────────

from feast import FeatureStore
import pandas as pd

fs = FeatureStore(repo_path='.')

# Define entities
entity_df = pd.DataFrame({
    'customer_id': [1001, 1002, 1003],
    'event_timestamp': [
        pd.Timestamp('2024-01-01'),
        pd.Timestamp('2024-01-01'),
        pd.Timestamp('2024-01-01')
    ]
})

# Get historical features
training_df = fs.get_historical_features(
    entity_df=entity_df,
    features=[
        'customer_features:age',
        'customer_features:income',
        'customer_features:credit_score'
    ]
).to_df()

print(training_df)

# ─────────────────────────────────────────────
# 4. ONLINE RETRIEVAL (SERVING)
# ─────────────────────────────────────────────

# Materialize features to online store
# feast materialize-incremental $(date +%Y-%m-%d)

# Get online features
entity_rows = [
    {'customer_id': 1001},
    {'customer_id': 1002}
]

online_features = fs.get_online_features(
    features=[
        'customer_features:age',
        'customer_features:income',
        'customer_features:credit_score'
    ],
    entity_rows=entity_rows
).to_dict()

print(online_features)
"""

print("✅ Feast Example")

# ═══════════════════════════════════════════
# TECTON
# ═══════════════════════════════════════════

"""
Tecton: Enterprise feature platform
- Real-time features
- Batch features
- Streaming features
- Feature monitoring
- Feature serving
"""

print("\n" + "="*60)
print("TECTON")
print("="*60)

"""
from tecton import Entity, FeatureView, BatchSource, materialization_context
from tecton.types import Field, String, Int64, Float64
from datetime import datetime, timedelta

# Define entity
customer = Entity(
    name='customer',
    join_keys=[Field('customer_id', Int64)]
)

# Define batch source
customer_source = BatchSource(
    name='customer_transactions',
    batch_config=FileConfig(
        uri='s3://bucket/transactions',
        file_format='parquet',
        timestamp_field='timestamp'
    )
)

# Define feature view
@batch_feature_view(
    sources=[customer_source],
    entities=[customer],
    mode='pandas',
    online=True,
    offline=True,
    feature_start_time=datetime(2024, 1, 1),
    batch_schedule=timedelta(days=1)
)
def customer_transaction_features(customer_source):
    return customer_source.groupby('customer_id').agg({
        'amount': ['sum', 'mean', 'count'],
        'is_fraud': 'sum'
    })

# Get features for training
training_data = customer_transaction_features.get_historical_features(
    spine=training_events
)

# Get features for serving
features = customer_transaction_features.get_online_features(
    join_keys={'customer_id': 1001}
)
"""

print("✅ Tecton Example")

# ═══════════════════════════════════════════
# HOPSWORKS FEATURE STORE
# ═══════════════════════════════════════════

"""
Hopsworks: Feature store with Python API
- Feature groups
- Training datasets
- Online serving
- Feature monitoring
"""

print("\n" + "="*60)
print("HOPSWORKS")
print("="*60)

"""
import hopsworks

# Connect to Hopsworks
project = hopsworks.login()
fs = project.get_feature_store()

# Create feature group
customer_fg = fs.create_feature_group(
    name='customer_features',
    version=1,
    description='Customer demographic features',
    primary_key=['customer_id'],
    event_time='timestamp'
)

# Insert features
customer_fg.insert(customer_df)

# Create training dataset
feature_view = fs.create_feature_view(
    name='customer_model_features',
    version=1,
    query=customer_fg.select(['age', 'income', 'credit_score'])
)

# Get training data
X_train, y_train = feature_view.training_data(
    training_dataset_version=1
)

# Get batch data
batch_data = feature_view.get_batch_data(
    start_time='2024-01-01',
    end_time='2024-01-31'
)

# Initialize online serving
feature_view.init_serving(training_dataset_version=1)

# Get online features
features = feature_view.get_feature_vector(
    entry={'customer_id': 1001}
)
"""

print("✅ Hopsworks Example")

print("\n" + "="*60)
print("Feature Stores Overview Complete")
print("="*60)
```

---

<div align="center">

## 🚀 Model Serving

</div>

### Deploy Models at Scale 🌐

```python
# ═══════════════════════════════════════════
# MODEL SERVING PLATFORMS
# ═══════════════════════════════════════════

"""
Model Serving: Deploy ML models for inference
- Low latency
- High throughput
- Scalability
- Model versioning
- A/B testing
"""

print("="*60)
print("MODEL SERVING")
print("="*60)

# ═══════════════════════════════════════════
# SELDON CORE
# ═══════════════════════════════════════════

"""
Seldon Core: ML deployment on Kubernetes
- Multi-framework support
- Canary deployments
- A/B testing
- Explainers
- Outlier detection
"""

print("\n" + "="*60)
print("SELDON CORE")
print("="*60)

"""
# 1. Create model class
class MyModel:
    def __init__(self):
        self.model = load_model()

    def predict(self, X, features_names=None):
        return self.model.predict(X)

# 2. Create Seldon deployment (YAML)
apiVersion: machinelearning.seldon.io/v1
kind: SeldonDeployment
metadata:
  name: my-model
spec:
  predictors:
  - name: default
    replicas: 3
    graph:
      name: classifier
      type: MODEL
      children: []
    componentSpecs:
    - spec:
        containers:
        - name: classifier
          image: mymodel:v1.0

# 3. Deploy
kubectl apply -f deployment.yaml

# 4. Send predictions
curl -X POST http://seldon-core/api/v1.0/predictions \
  -H 'Content-Type: application/json' \
  -d '{"data": {"ndarray": [[1, 2, 3, 4]]}}'
"""

print("✅ Seldon Core Example")

# ═══════════════════════════════════════════
# KSERVE (KFSERVING)
# ═══════════════════════════════════════════

"""
KServe: Serverless inference on Kubernetes
- Auto-scaling
- Canary rollouts
- Explainability
- Monitoring
"""

print("\n" + "="*60)
print("KSERVE")
print("="*60)

"""
# Inference service YAML
apiVersion: serving.kserve.io/v1beta1
kind: InferenceService
metadata:
  name: sklearn-iris
spec:
  predictor:
    sklearn:
      storageUri: gs://bucket/model
      resources:
        limits:
          cpu: 1
          memory: 2Gi
        requests:
          cpu: 100m
          memory: 1Gi

# Deploy
kubectl apply -f inference_service.yaml

# Predict
curl -X POST \
  http://sklearn-iris.default.example.com/v1/models/sklearn-iris:predict \
  -d '{"instances": [[6.8, 2.8, 4.8, 1.4]]}'
"""

print("✅ KServe Example")

# ═══════════════════════════════════════════
# RAY SERVE
# ═══════════════════════════════════════════

"""
Ray Serve: Scalable model serving
- Python-first
- Framework agnostic
- Dynamic batching
- Composition
"""

print("\n" + "="*60)
print("RAY SERVE")
print("="*60)

# Install: pip install ray[serve]

from ray import serve
import numpy as np

"""
# Define deployment
@serve.deployment(num_replicas=2)
class Classifier:
    def __init__(self):
        # Load model
        self.model = load_model()

    def __call__(self, request):
        data = request.query_params['data']
        prediction = self.model.predict(data)
        return {'prediction': prediction.tolist()}

# Start Ray Serve
serve.start()

# Deploy
Classifier.deploy()

# Query
import requests
response = requests.get(
    'http://localhost:8000/Classifier',
    params={'data': [1, 2, 3, 4]}
)
print(response.json())
"""

print("✅ Ray Serve Example")

# ═══════════════════════════════════════════
# NVIDIA TRITON
# ═══════════════════════════════════════════

"""
NVIDIA Triton: Multi-framework serving
- TensorFlow, PyTorch, ONNX
- GPU acceleration
- Dynamic batching
- Model ensemble
- Multiple protocols (HTTP, gRPC)
"""

print("\n" + "="*60)
print("NVIDIA TRITON")
print("="*60)

"""
# Model repository structure
model_repository/
└── my_model/
    ├── config.pbtxt
    └── 1/
        └── model.onnx

# config.pbtxt
name: "my_model"
platform: "onnxruntime_onnx"
max_batch_size: 8
input [
  {
    name: "input"
    data_type: TYPE_FP32
    dims: [ 4 ]
  }
]
output [
  {
    name: "output"
    data_type: TYPE_FP32
    dims: [ 1 ]
  }
]

# Start server
docker run --rm -p8000:8000 -p8001:8001 -p8002:8002 \
  -v /path/to/model_repository:/models \
  nvcr.io/nvidia/tritonserver:latest \
  tritonserver --model-repository=/models

# Client request
import tritonclient.http as httpclient
import numpy as np

client = httpclient.InferenceServerClient(url='localhost:8000')

inputs = httpclient.InferInput('input', [1, 4], 'FP32')
inputs.set_data_from_numpy(np.array([[1, 2, 3, 4]], dtype=np.float32))

outputs = httpclient.InferRequestedOutput('output')

results = client.infer('my_model', inputs=[inputs], outputs=[outputs])
output_data = results.as_numpy('output')
"""

print("✅ Triton Example")

print("\n" + "="*60)
print("Model Serving Overview Complete")
print("="*60)
```

---

<div align="center">

## 🏢 End-to-End Platforms

</div>

### Complete ML Platforms 🎯

```python
# ═══════════════════════════════════════════
# END-TO-END ML PLATFORMS
# ═══════════════════════════════════════════

"""
End-to-End Platforms: Complete ML lifecycle management
- Data preparation
- Model development
- Deployment
- Monitoring
- Collaboration
"""

print("="*60)
print("END-TO-END PLATFORMS")
print("="*60)

# ═══════════════════════════════════════════
# DATABRICKS
# ═══════════════════════════════════════════

"""
Databricks: Unified analytics platform
- Collaborative notebooks
- MLflow integration
- Delta Lake
- AutoML
- Model serving
"""

print("\n" + "="*60)
print("DATABRICKS")
print("="*60)

"""
from databricks import feature_store
from databricks.feature_store import FeatureStoreClient
import mlflow

# ─────────────────────────────────────────────
# 1. FEATURE ENGINEERING
# ─────────────────────────────────────────────

fs = FeatureStoreClient()

# Create feature table
fs.create_table(
    name='customer_features',
    primary_keys=['customer_id'],
    df=customer_df,
    description='Customer demographic features'
)

# ─────────────────────────────────────────────
# 2. MODEL TRAINING
# ─────────────────────────────────────────────

# Get features
training_set = fs.create_training_set(
    df=labels_df,
    feature_lookups=[
        FeatureLookup(
            table_name='customer_features',
            lookup_key='customer_id'
        )
    ],
    label='target'
)

training_df = training_set.load_df()

# Train with MLflow
with mlflow.start_run():
    model = train_model(training_df)

    # Log model with feature metadata
    fs.log_model(
        model,
        'model',
        flavor=mlflow.sklearn,
        training_set=training_set
    )

# ─────────────────────────────────────────────
# 3. MODEL SERVING
# ─────────────────────────────────────────────

# Register model
model_uri = f'runs:/{run_id}/model'
model_details = mlflow.register_model(model_uri, 'CustomerModel')

# Deploy to serving endpoint
# Via Databricks UI or API

# ─────────────────────────────────────────────
# 4. BATCH INFERENCE
# ─────────────────────────────────────────────

# Score batch
batch_df = fs.score_batch(
    model_uri=f'models:/CustomerModel/Production',
    df=new_customers_df
)
"""

print("✅ Databricks Example")

# ═══════════════════════════════════════════
# DATAIKU
# ═══════════════════════════════════════════

"""
Dataiku: Collaborative data science platform
- Visual workflows
- Code notebooks
- AutoML
- Deployment
- Monitoring
"""

print("\n" + "="*60)
print("DATAIKU")
print("="*60)

"""
import dataiku
from dataiku import pandasutils as pdu

# ─────────────────────────────────────────────
# 1. DATA PREPARATION
# ─────────────────────────────────────────────

# Get dataset
dataset = dataiku.Dataset('my_dataset')
df = dataset.get_dataframe()

# Prepare data
df_prepared = prepare_features(df)

# Write back
output_dataset = dataiku.Dataset('prepared_data')
output_dataset.write_with_schema(df_prepared)

# ─────────────────────────────────────────────
# 2. MODEL TRAINING
# ─────────────────────────────────────────────

from dataiku.ml import Model

# Train model
model = Model()
model.fit(X_train, y_train)

# Save model
model.save('my_model')

# ─────────────────────────────────────────────
# 3. DEPLOYMENT
# ─────────────────────────────────────────────

# Deploy as API endpoint
# Via Dataiku UI

# ─────────────────────────────────────────────
# 4. SCORING
# ─────────────────────────────────────────────

# Load model
model = Model.load('my_model')

# Score new data
predictions = model.predict(new_data)
"""

print("✅ Dataiku Example")

# ═══════════════════════════════════════════
# DOMINO DATA LAB
# ═══════════════════════════════════════════

"""
Domino: Enterprise MLOps platform
- Workspaces
- Experiments
- Model deployment
- Model monitoring
- Collaboration
"""

print("\n" + "="*60)
print("DOMINO DATA LAB")
print("="*60)

"""
from domino import Domino

# Initialize
domino = Domino('username/project')

# ─────────────────────────────────────────────
# 1. RUN EXPERIMENT
# ─────────────────────────────────────────────

# Submit training job
run = domino.runs_start(['python', 'train.py'],
                       title='Experiment 1',
                       tier='gpu')

# ─────────────────────────────────────────────
# 2. MODEL API
# ─────────────────────────────────────────────

# Deploy model as API
# Via Domino UI or CLI

# Call API
import requests
response = requests.post(
    'https://app.dominodatalab.com/v1/username/project/endpoint',
    json={'data': [1, 2, 3, 4]},
    headers={'X-Domino-Api-Key': 'YOUR_API_KEY'}
)
predictions = response.json()
"""

print("✅ Domino Example")

print("\n" + "="*60)
print("End-to-End Platforms Overview Complete")
print("="*60)
```

---

<div align="center">

## 📊 Platform Comparison

</div>

### Choose the Right Platform 🎯

```bash
# ═══════════════════════════════════════════
# COMPREHENSIVE PLATFORM COMPARISON
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CLOUD PLATFORMS COMPARISON               ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Feature           | AWS SageMaker    | Google Vertex AI | Azure ML       | IBM Watson   |
| ----------------- | ---------------- | ---------------- | -------------- | ------------ |
| **Ease of Use**   | ⭐⭐⭐           | ⭐⭐⭐⭐         | ⭐⭐⭐         | ⭐⭐         |
| **Cost**          | $$$              | $$$              | $$$            | $$$$         |
| **AutoML**        | ✅ Autopilot     | ✅ Built-in      | ✅ Built-in    | ✅ Built-in  |
| **Notebooks**     | ✅ Studio        | ✅ Workbench     | ✅ Compute     | ✅ Studio    |
| **Feature Store** | ✅ Yes           | ✅ Yes           | ❌ No          | ❌ No        |
| **Pipelines**     | ✅ Pipelines     | ✅ Pipelines     | ✅ Designer    | ✅ Flows     |
| **Serving**       | ✅ Endpoints     | ✅ Endpoints     | ✅ Endpoints   | ✅ Endpoints |
| **Monitoring**    | ✅ Model Monitor | ✅ Monitoring    | ✅ Monitoring  | ✅ OpenScale |
| **GPU Support**   | ✅ Excellent     | ✅ Excellent     | ✅ Excellent   | ✅ Good      |
| **Integration**   | ⭐⭐⭐⭐ AWS     | ⭐⭐⭐⭐ GCP     | ⭐⭐⭐⭐ Azure | ⭐⭐⭐ IBM   |
| **Best For**      | AWS users        | GCP users        | Azure users    | Enterprise   |

</div>

```bash
╔════════════════════════════════════════════════════════════╗
║                   AUTOML PLATFORMS                         ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Platform          | Type              | Speed    | Accuracy   | Cost     | Best For           |
| ----------------- | ----------------- | -------- | ---------- | -------- | ------------------ |
| **H2O.ai**        | Open + Commercial | ⭐⭐⭐⭐ | ⭐⭐⭐⭐   | Free/$$$ | Enterprise, Custom |
| **DataRobot**     | Commercial        | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | $$$$     | Enterprise         |
| **AutoGluon**     | Open-source       | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | Free     | Research, Kaggle   |
| **PyCaret**       | Open-source       | ⭐⭐⭐   | ⭐⭐⭐     | Free     | Quick prototyping  |
| **TPOT**          | Open-source       | ⭐⭐     | ⭐⭐⭐⭐   | Free     | Research           |
| **Google AutoML** | Cloud             | ⭐⭐⭐⭐ | ⭐⭐⭐⭐   | $$$      | GCP users          |

</div>

```bash
╔════════════════════════════════════════════════════════════╗
║                   MLOPS PLATFORMS                          ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Platform     | Learning Curve | Features   | Community       | Best For         |
| ------------ | -------------- | ---------- | --------------- | ---------------- |
| **MLflow**   | ⭐ Easy        | ⭐⭐⭐⭐   | ⭐⭐⭐⭐⭐ Huge | General purpose  |
| **Kubeflow** | ⭐⭐⭐ Hard    | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ Large  | Kubernetes users |
| **BentoML**  | ⭐⭐ Moderate  | ⭐⭐⭐     | ⭐⭐⭐ Growing  | Model serving    |
| **Seldon**   | ⭐⭐⭐ Hard    | ⭐⭐⭐⭐   | ⭐⭐⭐ Medium   | K8s deployment   |
| **Metaflow** | ⭐⭐ Moderate  | ⭐⭐⭐     | ⭐⭐⭐ Medium   | Netflix stack    |

</div>

```bash
╔════════════════════════════════════════════════════════════╗
║                   DECISION MATRIX                          ║
╚════════════════════════════════════════════════════════════╝

Choose Based On Your Needs:
─────────────────────────────────────────────────────────────

For Startups/Small Teams:
  1st: MLflow + Cloud ML (SageMaker/Vertex AI)
  2nd: Weights & Biases + Cloud
  Why: Low cost, easy to start, scales later

For Mid-Size Companies:
  1st: Databricks
  2nd: Cloud ML Platform + MLflow
  Why: Balance of features and cost

For Enterprises:
  1st: Databricks or Dataiku
  2nd: Domino Data Lab
  Why: Governance, collaboration, support

For Research Teams:
  1st: Weights & Biases
  2nd: MLflow
  Why: Experiment tracking, collaboration

For Heavy AWS Users:
  1st: SageMaker
  2nd: SageMaker + MLflow
  Why: Native AWS integration

For Heavy GCP Users:
  1st: Vertex AI
  2nd: Vertex AI + Kubeflow
  Why: Native GCP integration

For Kubernetes-Native:
  1st: Kubeflow
  2nd: Seldon Core
  Why: K8s-native, flexible

For AutoML Focus:
  1st: H2O.ai or DataRobot
  2nd: Google AutoML
  Why: Best AutoML capabilities

For Budget-Conscious:
  1st: MLflow (open-source)
  2nd: AutoGluon + Feast
  Why: Free, community-driven

For Rapid Prototyping:
  1st: Google Colab + W&B
  2nd: Kaggle + Neptune
  Why: Zero setup, free GPUs

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 💡 Best Practices

</div>

### Platform Implementation Guidelines 📋

```bash
# ═══════════════════════════════════════════
# ML PLATFORM BEST PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PLATFORM SELECTION                       ║
╚════════════════════════════════════════════════════════════╝

Evaluation Criteria:
─────────────────────────────────────────────────────────────
☐ Team size and skill level
☐ Budget constraints
☐ Existing infrastructure (cloud provider)
☐ Scalability requirements
☐ Security and compliance needs
☐ Integration requirements
☐ Support and maintenance
☐ Vendor lock-in concerns
☐ Feature requirements
☐ Time to value

Questions to Ask:
─────────────────────────────────────────────────────────────
• What's our current cloud provider?
• Do we have Kubernetes expertise?
• What's our monthly ML budget?
• How many models will we deploy?
• Do we need AutoML?
• What frameworks do we use?
• Do we need feature stores?
• How critical is monitoring?
• What's our team size?
• Do we need governance tools?

╔════════════════════════════════════════════════════════════╗
║                   IMPLEMENTATION STRATEGY                  ║
╚════════════════════════════════════════════════════════════╝

Phase 1: Experimentation (Month 1-2)
─────────────────────────────────────────────────────────────
✅ Start with experiment tracking (MLflow/W&B)
✅ Use cloud notebooks (Colab/SageMaker Studio)
✅ Version control code (Git)
✅ Document experiments
✅ Establish baselines

Phase 2: Infrastructure (Month 3-4)
─────────────────────────────────────────────────────────────
✅ Set up CI/CD pipelines
✅ Implement model registry
✅ Configure training infrastructure
✅ Set up data versioning (DVC)
✅ Establish monitoring

Phase 3: Production (Month 5-6)
─────────────────────────────────────────────────────────────
✅ Deploy first models
✅ Implement serving infrastructure
✅ Set up model monitoring
✅ Establish retraining pipelines
✅ Create dashboards

Phase 4: Scale (Month 7+)
─────────────────────────────────────────────────────────────
✅ Add feature store
✅ Implement A/B testing
✅ Optimize costs
✅ Automate workflows
✅ Team training

╔════════════════════════════════════════════════════════════╗
║                   COST OPTIMIZATION                        ║
╚════════════════════════════════════════════════════════════╝

Strategies:
─────────────────────────────────────────────────────────────
✅ Use spot instances for training
✅ Auto-scale serving endpoints
✅ Schedule notebook shutdowns
✅ Archive old experiments
✅ Use appropriate instance types
✅ Leverage free tiers
✅ Monitor usage regularly
✅ Set budget alerts
✅ Optimize model size
✅ Use model compression

Cost Comparison (Monthly):
─────────────────────────────────────────────────────────────
Minimal Setup:
  • MLflow (self-hosted): $50-100
  • Cloud compute: $200-500
  • Storage: $50-100
  Total: ~$300-700/month

Mid-Size Team:
  • Databricks: $2,000-5,000
  • Cloud compute: $1,000-3,000
  • Storage: $200-500
  Total: ~$3,200-8,500/month

Enterprise:
  • Platform license: $10,000-50,000
  • Cloud compute: $5,000-20,000
  • Storage: $1,000-5,000
  Total: ~$16,000-75,000/month

╔════════════════════════════════════════════════════════════╗
║                   SECURITY & GOVERNANCE                    ║
╚════════════════════════════════════════════════════════════╝

Security Checklist:
─────────────────────────────────────────────────────────────
☐ Role-based access control (RBAC)
☐ Secrets management (AWS Secrets Manager, etc.)
☐ Data encryption (at rest and in transit)
☐ Network isolation (VPC)
☐ Audit logging
☐ Model versioning
☐ Data lineage tracking
☐ Compliance (GDPR, HIPAA)
☐ Vulnerability scanning
☐ Regular security audits

Governance:
─────────────────────────────────────────────────────────────
✅ Model approval workflows
✅ Experiment documentation
✅ Model cards
✅ Reproducibility requirements
✅ Data quality checks
✅ Bias detection
✅ Performance thresholds
✅ Rollback procedures
✅ Incident response plans

╔════════════════════════════════════════════════════════════╗
║                   MONITORING & OBSERVABILITY               ║
╚════════════════════════════════════════════════════════════╝

What to Monitor:
─────────────────────────────────────────────────────────────
Model Performance:
  • Accuracy/precision/recall
  • Prediction latency
  • Throughput
  • Error rates

Data Quality:
  • Feature distributions
  • Missing values
  • Data drift
  • Outliers

System Health:
  • CPU/Memory usage
  • API response times
  • Queue lengths
  • Uptime

Business Metrics:
  • Model impact on KPIs
  • Cost per prediction
  • ROI
  • User satisfaction

Tools:
─────────────────────────────────────────────────────────────
• Grafana + Prometheus
• Datadog
• New Relic
• CloudWatch (AWS)
• Stackdriver (GCP)
• Application Insights (Azure)

╔════════════════════════════════════════════════════════════╗
║                   TEAM COLLABORATION                       ║
╚════════════════════════════════════════════════════════════╝

Best Practices:
─────────────────────────────────────────────────────────────
✅ Shared experiment tracking
✅ Code reviews for model code
✅ Documentation standards
✅ Regular sync meetings
✅ Knowledge sharing sessions
✅ Onboarding processes
✅ Runbooks for common tasks
✅ Clear ownership
✅ Communication channels

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔧 Implementation Guide

</div>

### Step-by-Step Platform Setup 🛠️

```python
# ═══════════════════════════════════════════
# COMPLETE PLATFORM IMPLEMENTATION
# ═══════════════════════════════════════════

"""
Example: Setting up an end-to-end ML platform
Stack: AWS SageMaker + MLflow + Feast
"""

print("="*60)
print("IMPLEMENTATION GUIDE")
print("="*60)

# ─────────────────────────────────────────────
# STEP 1: EXPERIMENT TRACKING
# ─────────────────────────────────────────────

"""
# Deploy MLflow on AWS
# 1. Create EC2 instance
# 2. Install MLflow
pip install mlflow boto3 psycopg2-binary

# 3. Start MLflow server
mlflow server \
    --backend-store-uri postgresql://user:pass@db.endpoint:5432/mlflow \
    --default-artifact-root s3://mlflow-artifacts/ \
    --host 0.0.0.0

# 4. Use in code
import mlflow

mlflow.set_tracking_uri('http://mlflow-server:5000')

with mlflow.start_run():
    mlflow.log_param('n_estimators', 100)
    mlflow.log_metric('accuracy', 0.95)
    mlflow.sklearn.log_model(model, 'model')
"""

# ─────────────────────────────────────────────
# STEP 2: TRAINING PIPELINE
# ─────────────────────────────────────────────

"""
# SageMaker training script
# train.py
import argparse
import mlflow
from sklearn.ensemble import RandomForestClassifier
import joblib

if __name__ == '__main__':
    parser = argparse.ArgumentParser()
    parser.add_argument('--n-estimators', type=int, default=100)
    parser.add_argument('--mlflow-tracking-uri', type=str)
    args = parser.parse_args()

    # Set MLflow tracking
    mlflow.set_tracking_uri(args.mlflow_tracking_uri)

    with mlflow.start_run():
        # Load data
        X_train, y_train = load_data()

        # Train model
        model = RandomForestClassifier(n_estimators=args.n_estimators)
        model.fit(X_train, y_train)

        # Log to MLflow
        mlflow.log_params({'n_estimators': args.n_estimators})
        mlflow.log_metric('train_accuracy', model.score(X_train, y_train))
        mlflow.sklearn.log_model(model, 'model')

        # Save for SageMaker
        joblib.dump(model, '/opt/ml/model/model.joblib')
"""

# ─────────────────────────────────────────────
# STEP 3: FEATURE STORE
# ─────────────────────────────────────────────

"""
# Set up Feast
# feature_store.yaml
project: my_project
registry: s3://feast-registry/registry.db
provider: aws
online_store:
    type: dynamodb
    region: us-west-2
offline_store:
    type: file

# features.py
from feast import Entity, Feature, FeatureView, FileSource
from datetime import timedelta

customer = Entity(name='customer', join_keys=['customer_id'])

customer_features = FeatureView(
    name='customer_features',
    entities=[customer],
    ttl=timedelta(days=1),
    schema=[
        Feature(name='age', dtype=Int64),
        Feature(name='income', dtype=Float32)
    ],
    source=FileSource(
        path='s3://bucket/features.parquet',
        timestamp_field='timestamp'
    )
)

# Apply features
feast apply
"""

# ─────────────────────────────────────────────
# STEP 4: MODEL SERVING
# ─────────────────────────────────────────────

"""
# Deploy model with SageMaker
import boto3
import sagemaker

sagemaker_session = sagemaker.Session()
role = sagemaker.get_execution_role()

# Create model from MLflow
model_uri = 'runs:/run-id/model'
model_data = mlflow.sagemaker.deploy(
    model_uri=model_uri,
    app_name='my-model',
    execution_role_arn=role,
    image_url='mlflow-pyfunc',
    region_name='us-west-2',
    mode='create'
)

# Endpoint configuration
predictor = sagemaker.Predictor(
    endpoint_name='my-model',
    sagemaker_session=sagemaker_session
)

# Make predictions
predictions = predictor.predict(test_data)
"""

# ─────────────────────────────────────────────
# STEP 5: MONITORING
# ─────────────────────────────────────────────

"""
# Set up monitoring with CloudWatch
import boto3

cloudwatch = boto3.client('cloudwatch')

# Custom metric
cloudwatch.put_metric_data(
    Namespace='ML/Models',
    MetricData=[
        {
            'MetricName': 'PredictionAccuracy',
            'Value': accuracy,
            'Unit': 'Percent',
            'Dimensions': [
                {'Name': 'ModelName', 'Value': 'my-model'},
                {'Name': 'ModelVersion', 'Value': 'v1'}
            ]
        }
    ]
)

# Set up alarms
cloudwatch.put_metric_alarm(
    AlarmName='ModelAccuracyLow',
    ComparisonOperator='LessThanThreshold',
    EvaluationPeriods=1,
    MetricName='PredictionAccuracy',
    Namespace='ML/Models',
    Period=300,
    Statistic='Average',
    Threshold=0.85,
    ActionsEnabled=True,
    AlarmActions=['arn:aws:sns:region:account:topic']
)
"""

print("\n" + "="*60)
print("Implementation Guide Complete")
print("="*60)
```

---

<div align="center">

## 📚 Resources & Learning

</div>

### Continue Your Platform Journey 🚀

```
📘 Official Documentation
   • AWS SageMaker: https://docs.aws.amazon.com/sagemaker/
   • Google Vertex AI: https://cloud.google.com/vertex-ai/docs
   • Azure ML: https://docs.microsoft.com/azure/machine-learning/
   • MLflow: https://mlflow.org/docs/
   • Kubeflow: https://www.kubeflow.org/docs/
   • Feast: https://docs.feast.dev/

📗 Books
   • Machine Learning Engineering (Andriy Burkov)
   • Designing Machine Learning Systems (Chip Huyen)
   • Building Machine Learning Powered Applications (Emmanuel Ameisen)

📙 Online Courses
   • Full Stack Deep Learning
   • Made With ML (MLOps)
   • Coursera MLOps Specialization

🎥 YouTube Channels
   • Weights & Biases
   • Made With ML
   • MLOps Community

💻 Communities
   • MLOps Community Slack
   • r/MachineLearning
   • r/MLOps
   • Kubeflow Slack
   • MLflow Slack

🛠️ Tools & Templates
   • Cookiecutter Data Science
   • MLOps Zoomcamp
   • Awesome MLOps (GitHub)
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

1. Start Simple
   • Begin with experiment tracking (MLflow/W&B)
   • Use cloud notebooks initially
   • Scale infrastructure as needed
   • Don't over-engineer early

2. Choose Based on Needs
   • Team size and skills
   • Budget constraints
   • Existing infrastructure
   • Scalability requirements

3. Focus on Core Components
   • Experiment tracking (essential)
   • Model registry (important)
   • Feature store (nice to have)
   • Serving platform (critical for production)
   • Monitoring (essential in production)

4. Iterate and Improve
   • Start with MVP
   • Get feedback
   • Add features incrementally
   • Optimize costs continuously

5. Invest in Team
   • Training and upskilling
   • Documentation
   • Best practices
   • Collaboration tools

"The best ML platform is the one your team actually uses." ✨

Platform Selection Priority:
─────────────────────────────────────────────────────────────
1. Experiment Tracking (Day 1)
2. Model Versioning (Week 1)
3. CI/CD for ML (Month 1)
4. Model Serving (Month 2)
5. Monitoring (Month 2)
6. Feature Store (Month 3+)
7. Advanced Automation (Month 6+)

═══════════════════════════════════════════════════════════
```

---

<div align="center">

**Built with 🚀 by MrDib, for ML practitioners**

_Remember: "MLOps is about getting ML into production and keeping it there!"_ 🌟

**Happy Platform Building!** 🛠️
