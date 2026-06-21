# Azure Cloud Fundamentals and Data Pipeline Implementation using Azure Data Factory

## 📌 Project Overview

This project demonstrates the implementation of an end-to-end data pipeline using **Microsoft Azure** and **Azure Data Factory (ADF)**. The pipeline reads a CSV file from Azure Blob Storage, validates its metadata, and copies it to another location within the storage account.

---

## 🎯 Objective

- Understand Azure Cloud fundamentals.
- Create and manage Azure resources.
- Build an ETL pipeline using Azure Data Factory.
- Learn Azure IAM role assignments.
- Validate file metadata before processing.
- Copy data from a source container to a destination container.

---

## 🛠️ Azure Services Used

- Azure Resource Group
- Azure Storage Account
- Azure Blob Storage
- Azure Data Factory
- Azure IAM (Identity and Access Management)

---

## 📂 Project Architecture

```
Sample-Superstore.csv
        │
        ▼
Source Blob Container (src)
        │
        ▼
Azure Data Factory
        │
        ├── Linked Service
        ├── Source Dataset
        ├── Get Metadata Activity
        └── Copy Data Activity
        │
        ▼
Destination Blob Container (des)
        │
        ▼
output.csv
```

---

## 📋 Project Tasks

### Task 1 – Resource Group

- Created Azure Resource Group.
- Organized Azure resources.

---

### Task 2 – Storage Setup

- Created Azure Storage Account.
- Created Blob Containers:
  - `src`
  - `des`
- Uploaded `Sample-Superstore.csv` to the source container.

---

### Task 3 – Azure Data Factory

- Created Azure Data Factory.
- Created Linked Service.
- Created Source Dataset.
- Created Destination Dataset.
- Configured Get Metadata Activity.

---

### Task 4 – Pipeline Development

Created a pipeline containing:

- Get Metadata Activity
- Copy Data Activity

Configured:

- Source Dataset
- Destination Dataset

---

### Task 5 – Pipeline Execution

- Validated Pipeline
- Published Changes
- Executed using Debug
- Verified Successful Execution

---

### Task 6 – IAM Roles

Configured Azure IAM Roles:

- Reader
- Storage Blob Data Contributor
- Managed Identity Access for Azure Data Factory

> **Note:** Contributor role may not be available in Azure for Students subscription.

---

## 📁 Project Structure

```
Azure-ADF-Data-Pipeline/
│
├── README.md
├── screenshots/
│   ├── resource-group.png
│   ├── storage-account.png
│   ├── blob-container.png
│   ├── linked-service.png
│   ├── source-dataset.png
│   ├── destination-dataset.png
│   ├── get-metadata.png
│   ├── pipeline-design.png
│   ├── pipeline-success.png
│   ├── iam-role.png
│   └── output-file.png
│
└── Sample-Superstore.csv
```

---

## 🔄 Pipeline Workflow

1. Read CSV file from Azure Blob Storage.
2. Validate file metadata using Get Metadata Activity.
3. Copy the CSV file using Copy Data Activity.
4. Save the copied file to the destination container.
5. Verify successful execution.

---

## ✅ Expected Output

- Source CSV successfully read.
- Metadata validated.
- File copied successfully.
- Pipeline execution status: **Succeeded**.
- Output file created in destination container.

---

## 📷 Screenshots Included

- Resource Group
- Storage Account
- Blob Container
- Linked Service
- Source Dataset
- Destination Dataset
- Get Metadata Activity
- Pipeline Design
- Successful Pipeline Execution
- IAM Role Assignment
- Output File

---

## 🚀 Technologies Used

- Microsoft Azure
- Azure Data Factory
- Azure Blob Storage
- Azure Portal
- CSV Files

---

## 📚 Learning Outcomes

After completing this project, the following concepts were understood:

- Azure Cloud Fundamentals
- Azure Resource Management
- Azure Blob Storage
- Azure Data Factory
- Linked Services
- Datasets
- Get Metadata Activity
- Copy Data Activity
- Azure IAM Roles
- End-to-End ETL Pipeline

---

## 👨‍💻 Author

**Laxmi Prasanna**

B.Tech Student  
CVR College of Engineering

---

## 📜 License

This project is created for educational and learning purposes.
