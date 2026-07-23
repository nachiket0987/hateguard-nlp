# 🛡️ HateGuard-NLP

### End-to-End Production-Ready Hate Speech Classification System using LSTM & Deep Learning

[![Python](https://img.shields.io/badge/Python-3.8-blue?logo=python&logoColor=white)](https://python.org)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange?logo=tensorflow&logoColor=white)](https://tensorflow.org)
[![Keras](https://img.shields.io/badge/Keras-LSTM-red?logo=keras&logoColor=white)](https://keras.io)
[![AWS](https://img.shields.io/badge/AWS-EC2%20%7C%20S3-yellow?logo=amazonaws&logoColor=white)](https://aws.amazon.com)
[![Docker](https://img.shields.io/badge/Docker-Containerized-blue?logo=docker&logoColor=white)](https://docker.com)
[![CircleCI](https://img.shields.io/badge/CircleCI-CI%2FCD-black?logo=circleci&logoColor=white)](https://circleci.com)

---

## 📌 Overview

**HateGuard-NLP** is a production-ready, end-to-end NLP pipeline that detects and classifies hate speech in text using a deep learning model built on LSTM (Long Short-Term Memory) neural networks. The project goes beyond experimentation — it includes data ingestion, validation, transformation, model training, evaluation, deployment to AWS EC2, and an interactive web interface.

> Built as a full MLOps pipeline — from raw data to a live deployed model.

---

## ✨ Key Features

- 🧠 **LSTM-Based Model** — Deep learning text classification with ~5M parameters
- 📦 **Modular ML Pipeline** — Clean component-based architecture (ingestion → validation → transformation → training → evaluation → deployment)
- ☁️ **AWS S3 Integration** — Remote model and artifact storage using S3 sync
- 🐳 **Dockerized** — Fully containerized for consistent deployment
- 🔄 **CI/CD with CircleCI** — Automated build, test, and deployment on every push
- 🚀 **Deployed on AWS EC2** — Live production environment with self-hosted runner
- 🌐 **Flask Web App** — Simple UI to test hate speech classification in real time
- 📊 **Imbalanced Data Handling** — Combined 2 Kaggle datasets to create a balanced training set

---

## 🏗️ Architecture

```
Raw Data (Kaggle)
        │
        ▼
┌─────────────────┐
│  Data Ingestion │  ← Downloads & stores dataset from S3
└────────┬────────┘
         │
         ▼
┌──────────────────────┐
│  Data Validation     │  ← Checks schema & data quality
└──────────┬───────────┘
           │
           ▼
┌──────────────────────────┐
│  Data Transformation     │  ← Tokenization, lowercasing, stopword removal
└──────────────┬───────────┘
               │
               ▼
┌──────────────────────────┐
│  Model Training          │  ← LSTM + Keras Embedding Layer
└──────────────┬───────────┘
               │
               ▼
┌──────────────────────────┐
│  Model Evaluation        │  ← Compare against best model
└──────────────┬───────────┘
               │
               ▼
┌──────────────────────────┐
│  Model Pusher            │  ← Push best model to AWS S3
└──────────────┬───────────┘
               │
               ▼
┌──────────────────────────┐
│  Flask App (app.py)      │  ← Serve predictions via web UI
└──────────────────────────┘
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Language** | Python 3.8 |
| **Deep Learning** | TensorFlow, Keras (LSTM) |
| **Data Processing** | Pandas, NumPy, NLTK |
| **Web App** | Flask |
| **Cloud Storage** | AWS S3 |
| **Deployment** | AWS EC2 |
| **Containerization** | Docker |
| **CI/CD** | CircleCI |
| **Experiment Tracking** | Jupyter Notebook |

---

## 📁 Project Structure

```bash
HateGuard-NLP/
├── .circleci/
│   └── config.yml                  # CircleCI CI/CD pipeline
├── hate/                           # Main source package
│   ├── components/
│   │   ├── data_ingestion.py
│   │   ├── data_validation.py
│   │   ├── data_transformation.py
│   │   ├── model_trainer.py
│   │   ├── model_evaluation.py
│   │   └── model_pusher.py
│   ├── configuration/
│   │   └── s3_syncer.py
│   ├── constants/
│   │   └── __init__.py
│   ├── entity/
│   │   ├── config_entity.py
│   │   └── artifact_entity.py
│   ├── exception/
│   │   └── __init__.py
│   ├── logger/
│   │   └── __init__.py
│   ├── ml/
│   │   └── model.py
│   └── pipeline/
│       ├── train_pipeline.py
│       └── prediction_pipeline.py
├── Notebook/
│   └── Hate_speech_experiment.ipynb
├── data/
│   └── dataset.zip
├── app.py                          # Flask web application
├── Dockerfile
├── requirements.txt
├── setup.py
└── template.py                     # Project scaffolding script
```

---

## ⚙️ Local Setup

### 1. Clone the Repository
```bash
git clone https://github.com/nachiket0987/hateguard-nlp.git
cd hateguard-nlp
```

### 2. Create & Activate Conda Environment
```bash
conda create -n hateguard python=3.8 -y
conda activate hateguard
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Set AWS Environment Variables
```bash
export AWS_ACCESS_KEY_ID="your-access-key-id"
export AWS_SECRET_ACCESS_KEY="your-secret-access-key"
export AWS_DEFAULT_REGION="us-east-1"
```

### 5. Run Training Pipeline
```bash
python app.py
```
Navigate to `http://localhost:8080` and trigger training from the UI.

---

## 🐳 Docker Setup

```bash
# Build the image
docker build -t hateguard-nlp .

# Run the container
docker run -p 8080:8080 hateguard-nlp
```

---

## 🔄 CI/CD Pipeline (CircleCI → AWS EC2)

1. **CircleCI** detects a push to `main` branch
2. Runs the automated build & test pipeline
3. Builds and pushes the Docker image
4. Connects to the **self-hosted EC2 runner**
5. Pulls the latest image and restarts the container

### Deployment Steps
1. Set up a CircleCI account and connect your GitHub repo
2. Launch an EC2 instance and install the self-hosted runner
3. Configure environment variables in CircleCI project settings:
   - `AWS_ACCESS_KEY_ID`
   - `AWS_SECRET_ACCESS_KEY`
   - `AWS_DEFAULT_REGION`
4. Push to `main` — deployment triggers automatically ✅

---

## 🧬 ML Pipeline Workflow

```
Update Constants → Update Entity → Update Component → Update Pipeline → Test App
```

---

## 📊 Model Details

| Parameter | Value |
|-----------|-------|
| **Architecture** | LSTM |
| **Embedding** | Keras Embedding Layer |
| **Total Parameters** | ~5,080,501 |
| **Training Data** | 2 combined Kaggle datasets |
| **Problem Type** | Binary Classification (Hate / Non-Hate) |
| **Preprocessing** | Tokenization, Lowercasing, Stopword Removal |

---

## 👤 Author

**Nachiket Gadilohar**
- 📧 Email: [nachiketlohar0306@gmail.com](mailto:nachiketlohar0306@gmail.com)
- 💻 GitHub: [@nachiket0987](https://github.com/nachiket0987)
- 🔗 LinkedIn: [nachiket-gadilohar-profile](https://www.linkedin.com/in/nachiket-gadilohar-profile/)

---

## ⭐ If you found this useful, consider giving it a star!
