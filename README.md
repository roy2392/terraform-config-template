# Modular AWS Infrastructure with Terraform

## Purpose

This repository provides a clean, modular Terraform configuration to initialize and manage AWS infrastructure. It demonstrates best practices for organizing Terraform code, separating sensitive information, and using variables effectively.

The infrastructure includes:
- A VPC
- An Internet Gateway
- A custom Route Table
- A Subnet
- Security Groups
- A Network Interface
- An Elastic IP
- An EC2 instance with Apache2 installed

## Prerequisites

- Terraform installed (version 0.12+)
- AWS CLI configured
- An AWS account with necessary permissions

## File Structure

- `main.tf`: Contains the main Terraform configuration
- `terraform.tfvars`: Stores non-sensitive configuration variables
- `.env`: Stores sensitive AWS credentials (not to be committed to version control)
- `README.md`: This file, containing usage instructions

## Setup Instructions

1. Clone this repository:
        ```bash
        git clone https://github.com/roy2392/terraform-config-template.git
        git clone terraform-config-template
        ```


2. Create a `.env` file in the root directory with your AWS credentials:
        ```bash
        AWS_ACCESS_KEY=your_access_key
        AWS_SECRET_KEY=your_secret_key
        ```

3. Update `terraform.tfvars` with your desired configuration:
        ```bash
        region = "us-east-1"
        key_name = "your-key-name"
        availability_zone = "for example: us-east-1a"
        ```

## Usage

Follow these steps to initialize and apply your Terraform configuration:

1. Source the environment variables:
```bash
export $(cat .env | xargs)
```
This step loads your AWS credentials from the .env file.
2. Set Terraform environment variables:
```bash
export TF_VAR_aws_access_key=$AWS_ACCESS_KEY
export TF_VAR_aws_secret_key=$AWS_SECRET_KEY
```
This step makes your AWS credentials available to Terraform.
3. Initialize Terraform:
```bash
terraform init
```
This command initializes Terraform, downloading necessary providers and modules.
4. Plan your infrastructure:
```bash
terraform plan -var-file=terraform.tfvars
```
This command shows you what changes Terraform will make to your infrastructure.
5. Apply the changes:
```bash
terraform apply -var-file=terraform.tfvars
```
Security Note
Never commit the .env file or any file containing sensitive information to version control. Make sure to add .env to your .gitignore file.
Contributing
Contributions to improve this configuration are welcome. Please submit a pull request or open an issue to discuss proposed changes.








        



