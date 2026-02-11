# Event Driven Architecture Project with AWS

This project demonstrates a simple Event Driven ETL pipeline using AWS services.  
It processes CSV files uploaded to a Source S3 bucket and stores the transformed output in a Target S3 bucket using SNS, SQS, and Lambda.

---

## 📌 Architecture Overview

Source S3 (CSV) → SNS → SQS → Lambda → Target S3

<img width="585" height="562" alt="architecture-diagram" src="https://github.com/user-attachments/assets/13433e91-26f3-40bb-aa33-e5cc0a1e0e48" />


The system follows an event driven model where each new object upload automatically triggers the processing pipeline.

---

## 🏗️ Components and Roles

### 🔹 Event Producer
**Amazon S3** acts as the event producer, generating events whenever a file is uploaded, modified, or deleted.

### 🔹 Event Ingestion
**Amazon SNS** acts as the ingestion layer, capturing events from S3 and distributing them to subscribers.

### 🔹 Event Stream
**Amazon SQS** functions as the event stream, buffering and storing messages from SNS to ensure reliable and decoupled processing.

### 🔹 Event Consumer
**AWS Lambda** serves as the event consumer, triggered by messages in SQS to process data and execute transformation logic.

### 🔹 Event Sink
The **Target S3 bucket** acts as the event sink, storing processed data from Lambda and completing the ETL workflow.

---

## 🔄 Workflow

1. A CSV file is uploaded to the Source S3 bucket.
2. S3 triggers an event notification to SNS.
3. SNS forwards the event to the SQS queue.
4. Lambda polls SQS and processes the message.
5. Processed data is stored in the Target S3 bucket.

---

## ⚙️ ETL Breakdown

### Extract
Lambda reads raw CSV data from the Source S3 bucket.

### Transform
Data is cleaned and transformed according to business logic.

### Load
Processed data is stored in the Target S3 bucket.

---

## 🛠️ Technologies Used

- Amazon S3  
- Amazon SNS  
- Amazon SQS  
- AWS Lambda  
- Python  

---

## 🎯 Project Goals

- Understand Event Driven Architecture  
- Implement service decoupling  
- Build a scalable ETL pipeline  
- Practice Cloud Data Engineering concepts  

---
