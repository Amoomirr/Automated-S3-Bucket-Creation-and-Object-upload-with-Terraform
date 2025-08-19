# Automated S3 Bucket Creation and Object Upload using Terraform

This project demonstrates the use of Terraform for automating AWS S3 bucket creation and object management. Terraform is an open-source Infrastructure as Code (IaC) tool that allows you to define and provision cloud resources declaratively using configuration files.

Using this Terraform configuration, the S3 bucket and associated objects are secure, server-side encryption and blocks all public access. Additionally, the project automates the upload of multiple files into the bucket while maintaining folder structures.
---

## 📌 **Project Overview**

- **Goal:** Automate the creation of an AWS S3 bucket and upload files using Terraform.
- **Key Features:**
  - Secure bucket creation with **block public access** enabled.
  - **Server-side encryption** for all objects.
  - Upload multiple files while maintaining folder structure.
- **Tools & Technologies:**  
  - **AWS Services:** S3, IAM  
  - **Terraform:** Infrastructure as Code (IaC)  
  - **AWS CLI**  
  - **Linux (WSL)**  

---

## ✅ **Prerequisites**

- **AWS Account** with IAM user credentials (Access Key & Secret Key)
- **Terraform** 
- **AWS CLI** installed and configured
- **Basic knowledge of AWS & Terraform**

---

## 🛠 **Setup Instructions**

### **Step 1: Create IAM User and Attach Policy**
- Create an **IAM User** with least privilege permissions.
  <img width="1563" height="743" alt="IAM-User" src="https://github.com/user-attachments/assets/e6f2eb26-7f53-48b6-9170-99f6925f19c6" />
- Attach a custom policy (`TerraformS3LimitedAccess`) granting S3 access.
  <img width="485" height="415" alt="IAM-Policy" src="https://github.com/user-attachments/assets/7aba6617-dc15-4ae1-aa95-95237acff4ab" />

- After bucket creation, restrict the policy to the specific **bucket ARN** for better security.
  


---

### **Step 2: Install Terraform**
- Install Terraform on **WSL/Linux**:
  ```bash
  terraform --version
  ```
  [Terraform Installation Guide](https://developer.hashicorp.com/terraform/install)

---

### **Step 3: Configure AWS CLI**
- Run the following command and enter your **Access Key**, **Secret Key**, and **Region**:
  ```bash
  aws configure
  ```
- Example:
  ```
  AWS Access Key ID: <your-access-key>
  AWS Secret Access Key: <your-secret-key>
  Default region name: ap-south-1
  Default output format: json
  ```
<img width="953" height="442" alt="aws-configure" src="https://github.com/user-attachments/assets/aa9fc6ab-959c-4491-93e2-37bc5672f8b4" />

---

### **Step 4: Create Terraform Configuration**
- Create a **project directory** and add `main.tf` file with the required configuration.
<img width="1901" height="752" alt="terraform-code" src="https://github.com/user-attachments/assets/4aa6fe7e-b56b-4a7a-89b0-5a089bbdf8a9" />

---

### **Step 5: Initialize and Apply Terraform**
- Initialize the working directory:
  ```bash
  terraform init
  ```
- Preview the execution plan:
  ```bash
  terraform plan
  ```
- Apply the configuration:
  ```bash
  terraform apply
  ```
<img width="1681" height="721" alt="terraform-apply" src="https://github.com/user-attachments/assets/fe83377a-99c7-4f85-bcbd-613532f0de31" />

---

### **Step 6: Verify Resources**
- Verify the S3 bucket and uploaded objects via **AWS CLI**:
  ```bash
  aws s3 ls
  aws s3 ls s3://<bucket-name>
  ```
<img width="952" height="257" alt="s3-objects-cmd" src="https://github.com/user-attachments/assets/83dfa746-8c59-4e71-b219-9761886f7b97" />

---

## 🔐 **Security Best Practices**
- Enable **block public access** for S3 bucket.
- Use **server-side encryption** (SSE-S3).
- Restrict IAM policy to the specific bucket **ARN** after creation.

---

## ✅ **Project Outcome**
- IAM user configured with least privilege.
- S3 bucket created and files uploaded automatically.
- Security enforced (encryption, no public access).
- Verified via AWS CLI and Management Console.
  
<img width="1110" height="418" alt="object_upload2" src="https://github.com/user-attachments/assets/e349eacf-6c86-4c0c-8a4e-be038abff323" />

---

## 📚 **References**
- [Terraform Documentation](https://developer.hashicorp.com/terraform/docs)
- [AWS S3 Documentation](https://docs.aws.amazon.com/s3/)
- [AWS CLI Documentation](https://docs.aws.amazon.com/cli/)
