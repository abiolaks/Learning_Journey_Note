# Working with Azure Services f

# 📘 Uploading to Azure Blob Storage with Azure Identity (Python)

This guide shows how to upload files to Azure Blob Storage securely using Azure Identity (no connection strings or keys hardcoded).

---

## 🔧 Prerequisites

- Azure Storage Account created
- Blob container (e.g., `employeedata001`) exists
- Logged into Azure CLI (`az login`) or VS Code with Azure extension
- Python environment with these packages installed:

```bash
pip install azure-identity azure-storage-blob

🔐 Grant Role: Storage Blob Data Contributor
Your Azure user must be granted permission to write blobs:

Go to Azure Portal

Navigate to your Storage Account

Open Access Control (IAM) → Add role assignment

Choose Role: Storage Blob Data Contributor

Assign to your User, Group, or Service Principal

Click Review + Assign

🕓 Changes may take a few minutes to take effect

🚀 Upload File to Blob Storage (Python)
python
Copy
Edit
from azure.identity import DefaultAzureCredential
from azure.storage.blob import BlobClient

# === Settings ===
account_url = "https://<your-storage-account-name>.blob.core.windows.net"
container_name = "employeedata001"
blob_name = "employee_data.csv"
local_file_path = r"C:\path\to\employee_data.csv"

# === Authenticate ===
credential = DefaultAzureCredential()

# === Upload ===
blob = BlobClient(
    account_url=account_url,
    container_name=container_name,
    blob_name=blob_name,
    credential=credential
)

with open(local_file_path, "rb") as data:
    blob.upload_blob(data, overwrite=True)

print("✅ Upload successful!")
📂 List All Blobs in a Container
python
Copy
Edit
from azure.storage.blob import ContainerClient

container_client = ContainerClient(
    account_url=account_url,
    container_name=container_name,
    credential=credential
)

print("📦 Blobs in container:")
for blob in container_client.list_blobs():
    print(blob.name)
🧪 Local Testing Checklist
✅ Logged in via az login or VS Code Azure extension

✅ User has correct RBAC role

✅ Storage account and container exist

✅ File path is correct and accessible

🧰 Useful Links
Azure Blob Storage Python SDK Docs

DefaultAzureCredential Info

Assign Roles in Azure
