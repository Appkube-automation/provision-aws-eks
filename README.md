# EKS Provisiong Usig Terraform

Create customize kubernetes cluster on Amazon Cloud.


## S3 Backend

To configure s3 as a Backend storage for terraform state file. Add the below code to main.tf with appropriate bucket name and file name.

```bash
 terraform {
  backend "s3" {
    bucket = "mybucket"
    key    = "path/to/my/key.tfstate"
    region = "us-east-1"
  }
}
```
This can also be done at the run time by using switches in terraform init command.

```bash
terraform init -backend-config="bucket=mybucket" -backend-config="key=path/to/key.tfstate" -backend-config="region=us-east-1"
```
## Environment Variables

To run this project, you will need to add the following environment variables to your .tfvars file


| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:
|Region|AWS Region to deploy cluser|Sring|US-east-1|yes
|cluster_name|Eks Cluster name|string|N/A|yes|
|cluster_version|Kubernetes Version to deploy|number|N/A|yes




## Run Locally

Clone the project

```bash
  git clone https://github.com/synectiks-sddc/provision-aws-eks.git  
```

Go to the project directory

```bash
  cd provision-aws-eks
```

Initiate Repository

```bash
  terraform init
```

Dry Run the script for assessing the changes being applied to the infrastructure.

```bash
 terraform plan
```
Apply the changes

```bash
 terraform apply
```

## Required software Versions

- kubectl client version 1.23
- Terraform version v1.1.6