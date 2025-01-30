# AWS Infrastructure with Terraform

This repository contains Infrastructure as Code (IaC) using Terraform to set up a complete AWS Virtual Private Cloud (VPC) environment. If you're familiar with Python, think of this as "infrastructure development" where the code defines your cloud resources instead of application logic.

## What Does This Do?

This Terraform configuration automatically creates a production-ready VPC setup in AWS, similar to how you might use Python's environment management to set up your development environment. Here's what it creates:

### Core Infrastructure Components

1. **VPC (Virtual Private Cloud)**
   - Like creating a virtual isolated network (similar to setting up a virtual environment in Python)
   - Default CIDR block: 10.0.0.0/16 (configurable in variables.tf)

2. **Subnets**
   - 3 Private Subnets (like having protected environments for your databases)
   - 3 Public Subnets (like having environments exposed to the internet for your web applications)
   - Similar to how you might separate your Python application into different modules for security

3. **Network Components**
   - Internet Gateway (IGW) - Like your router to the internet
   - NAT Gateway - Like a proxy server for private resources to access the internet
   - Route Tables - Like routing rules for your network traffic

## Getting Started

### Prerequisites

1. AWS Account
2. Terraform installed (similar to how you'd need Python installed)
3. AWS CLI configured with appropriate credentials

### Configuration Files

- `main.tf`: The main infrastructure code (think of it as your Python `main.py`)
- `variables.tf`: Variable definitions (similar to configuration variables in Python)
- `.github/workflows/terraform.yml`: GitHub Actions workflow for automated deployment

### Usage

```bash
# Initialize Terraform (similar to creating a virtual environment)
terraform init

# Format the code (similar to using Black in Python)
terraform fmt

# Preview changes (like doing a dry run)
terraform plan

# Apply changes (like deploying your Python application)
terraform apply
```

## Structure for Python Developers

If you're familiar with Python project structure, here's how this Terraform project maps to concepts you know:

```
Python                     Terraform
----------------          ----------------
requirements.txt    →     required_providers in terraform block
main.py            →     main.tf
config.py          →     variables.tf
.env              →     terraform.tfvars (not shown in repo)
pytest            →     terraform plan
deployment        →     terraform apply
```

## GitHub Actions Integration

The included GitHub Actions workflow provides automated infrastructure deployment, similar to how you might use CI/CD for your Python applications. It:

1. Runs on push to main branch or pull requests
2. Automatically formats code
3. Validates infrastructure changes
4. Applies changes when merged to main

## How to Use This With Your Python Applications

This infrastructure is perfect for deploying Python web applications, ML models, or data processing pipelines:

- Private subnets can host your databases or ML training environments
- Public subnets can host your Flask/FastAPI web services
- NAT Gateway allows private resources to download packages and updates

### Example Use Cases

1. **ML Model Deployment**
   - Deploy your scikit-learn models in private subnets
   - Expose prediction APIs in public subnets

2. **Data Processing Pipeline**
   - Run Pandas/NumPy processing jobs in private subnets
   - Store results in databases hosted in private subnets

3. **Web Applications**
   - Host your Flask/Django apps in public subnets
   - Keep your databases secure in private subnets

## Variables and Customization

You can customize the infrastructure by modifying `variables.tf`, similar to how you'd use environment variables in Python:

- `aws_region`: AWS region for deployment (default: us-east-1)
- `vpc_name`: Name of your VPC
- `vpc_cidr`: IP range for your VPC
- `private_subnets`: Configuration for private subnets
- `public_subnets`: Configuration for public subnets

## Security Considerations

- Private subnets are not directly accessible from the internet (like using private methods in Python)
- Public subnets can be accessed from the internet (like public API endpoints)
- NAT Gateway provides secure outbound internet access for private resources

## Best Practices

1. Version control your Terraform code (just like your Python code)
2. Use variables for customization
3. Follow the principle of least privilege
4. Always review `terraform plan` output before applying changes
5. Use workspaces for different environments (dev/staging/prod)

## Troubleshooting

Common issues and solutions:

1. **Initialization Failures**
   - Check AWS credentials
   - Verify Terraform installation

2. **Apply Failures**
   - Check for resource name conflicts
   - Verify AWS service limits
   - Check for dependent resources

Need help? Refer to:
- [Terraform Documentation](https://www.terraform.io/docs)
- [AWS Documentation](https://docs.aws.amazon.com)