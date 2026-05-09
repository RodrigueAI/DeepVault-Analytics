# DeepVault Analytics: Enterprise-Scale ML Pipeline

## 🚀 Overview

DeepVault Analytics is a professional-grade data science and engineering project designed to showcase how to bridge the gap between robust enterprise data warehousing and high-performance deep learning.

Most ML projects start with a flat CSV. This project starts with raw, chaotic data (Amazon Reviews & GDELT Events) and processes it through a scalable Data Vault 2.0 architecture, serving features via a Feature Store to a Distributed PyTorch model.

---

## 🏗️ Architecture

The system is built on four main pillars:

1. **Ingestion Layer**  
   Streaming and batch ingestion from Hugging Face (Amazon Reviews) and GDELT API using PySpark.

2. **Storage Layer (Data Vault 2.0)**  
   Implementation of Hubs, Links, and Satellites in Parquet format to ensure auditability and scalability.

3. **Feature Store (Feast)**  
   Decoupling feature engineering from model training, providing a unified interface for online/offline features.

4. **Intelligence Layer (PyTorch)**  
   A deep learning model for sentiment analysis and event prediction, leveraging the processed enterprise data.

---

## 🛠️ Tech Stack

- **Data Processing:** Apache Spark (PySpark)
- **Data Modeling:** Data Vault 2.0 (Hub-Link-Satellite)
- **Storage Format:** Apache Parquet / Delta Lake
- **Feature Management:** Feast (Feature Store)
- **Machine Learning:** PyTorch
- **Containerization:** Docker & Docker Compose

---

## 📂 Project Structure

```bash
.
├── data-engineering/         # Spark jobs for Raw -> Vault -> Features
│   ├── vault_transform/      # Hub/Link/Satellite logic
│   └── feature_extraction/   # Feature engineering scripts
├── feature-store/            # Feast definitions and registries
├── ml-modeling/              # PyTorch architecture & training loops
│   ├── networks/             # Model definitions (Transformers/RNNs)
│   └── training/             # Distributed training scripts
├── infrastructure/           # Docker-compose & environment configs
└── notebooks/                # Exploratory Data Analysis (EDA)
```

---

## 🌟 Key Features

### ✅ Audit-Ready Data

Unlike traditional OBT (One Big Table) approaches, the Data Vault allows tracking every change in the Amazon Review metadata over time.

### ✅ Scalable Feature Engineering

Using Spark to handle millions of rows, ensuring the pipeline remains performant as the dataset grows.

### ✅ Point-in-Time Correctness

Using Feast to prevent data leakage during training by fetching features exactly as they were at the time of the event.

---

## 🚦 Getting Started

### 1. Clone the Repository

```bash
git clone <repository-url>
cd deepvault-analytics
```

### 2. Start the Infrastructure

```bash
docker-compose up -d
```

This starts:

- Spark Master
- Spark Workers
- Postgres (Vault metadata storage)

### 3. Run the Data Ingestion

```bash
spark-submit data-engineering/ingestion/load_amazon.py
```

### 4. Train the Model

```bash
python ml-modeling/training/train.py
```

---

## 📈 Future Roadmap

- [ ] Implement a CI/CD pipeline for automated model re-training
- [ ] Add a FastAPI endpoint to serve the PyTorch model in real-time
- [ ] Integrate MLflow for experiment tracking

---

## 📜 License

MIT License

---

## 🤝 Contributing

Contributions, ideas, and improvements are welcome. Feel free to open issues or submit pull requests.
