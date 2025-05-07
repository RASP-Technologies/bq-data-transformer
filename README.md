# bq-data-transformer

---

## ⚙️ Prerequisites

- Python 3.10+
- A Google Cloud project with:
    - A BigQuery dataset
    - A GCS bucket
    - A service account with roles:
        - `BigQuery Data Editor`
        - `Storage Object Admin`
- Service account key in JSON format

---

## 🛠️ Installation

1. **Clone the repository**:

```bash
git clone https://github.com/RASP-Technologies/bq-data-transformer.git
cd bq-data-transformer

---

## 📜 Minimum IAM Roles Required for GCP Service Account

To allow the service account to interact with GCS and BigQuery in a secure, least-privilege way, assign the following roles:

### 📁 1. Google Cloud Storage Access
To **read and write Parquet files** to a GCS bucket:

- **Option A (simpler):**
    - `roles/storage.objectAdmin` on the **specific bucket**

- **Option B (more restrictive):**
    - `roles/storage.objectCreator` – for writing files
    - `roles/storage.objectViewer` – for reading files

> **Note:** It is recommended to grant these roles at the **bucket level** rather than project-wide.

---

### 📊 2. BigQuery Access
To **create external tables** and **query data** in BigQuery:

- `roles/bigquery.dataEditor` – to create external tables and manage table metadata
- `roles/bigquery.user` – to run queries and interact with datasets

> If only read access is needed and no tables are being created, consider using:
> - `roles/bigquery.dataViewer`

## 🧪 Quickstart Guide

Follow these steps to set up and run the `trulens_data_transformer` application.

---

### ⚙️ Configuration

Edit the `config/config.ini` file with your GCP environment details:

```ini
[general]
project_id = <your-gcp-project-id>
dataset_id = <your-bigquery-dataset>
region = <your-gcp-region>
bucket_name = <your-gcs-bucket>
input_folder = input_folder // Keep this as it is
gcs_output_uri = <output-gcs-uri>
service_account_json = <path-to-service-account-json>
```
### 🚀 Installation & Execution

#### Create a virtual environment
```
python3.12 -m venv venv
source venv/bin/activate
```

#### Install the application from the wheel file
```pip install dist/trulens_data_transformer-1.0.0-py3-none-any.whl```

#### Run the application
```bq_recommendation```



