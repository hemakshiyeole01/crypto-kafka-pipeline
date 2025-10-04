# Crypto Kafka Pipeline

## Project Overview
This project is an end-to-end **real-time cryptocurrency data pipeline** using **Kafka, Python, and MongoDB**. It allows you to:  
- Produce cryptocurrency data streams with Python (`producer.py`)  
- Consume data streams in real-time (`consumer.py`)  
- Store data in **MongoDB** for further analysis  

The system is fully containerized using **Docker** for easy deployment.

---

## Features
- Real-time data streaming with **Kafka**
- Python producer and consumer integration
- Storage in MongoDB for persistence
- Works offline locally using Docker containers
- Easily extendable for additional crypto data sources or analytics

---

## Prerequisites
- Python 3.12+  
- Docker & Docker Compose  
- Virtual environment (optional, but recommended)  

Python dependencies (install via `pip install -r requirements.txt`):
- `kafka-python`  
- `pymongo`  

---
## Project Structure

📁 crypto-kafka-pipeline/

 ├── docker-compose.yml
 
 ├── producer/
 
 │   └── producer.py
 
 ├── stream/
 
 │   └── stream_processor.py
 
 ├── consumer/
 
 │   └── consumer.py
 
 ├── requirements.txt
 
 └── README.md


## Setup and Running

### 1. Start Docker Containers
docker-compose up -d zookeeper mongodb kafka
Check that containers are running:
docker ps

### 2. Activate Python Virtual Environment
python -m venv .venv
.\.venv\Scripts\activate    # Windows
source .venv/bin/activate   # Linux/Mac
pip install -r requirements.txt

### 3. Run Producer
python producer.py
This sends crypto data messages to the Kafka topic.

### 4. Run Consumer
python consumer.py
The consumer reads messages from Kafka and stores them in MongoDB.

### 5. Verify MongoDB Data
Enter the MongoDB shell:
docker exec -it mongodb mongosh
Switch to the database and check inserted data:
use crypto_db
db.crypto_data.find().pretty()
