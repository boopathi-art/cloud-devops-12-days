\# Day 6 – Terraform \& AWS IAM Practice



\## 📌 Overview



Today I practiced \*\*Terraform\*\* for Infrastructure as Code (IaC) and used the \*\*AWS provider\*\* to create an AWS IAM user.



\## 🛠️ Tools Used



\* Terraform

\* AWS

\* AWS IAM

\* AWS Provider

\* Command Prompt

\* Git \& GitHub



\## 📚 Topics Covered



\* Terraform initialization

\* Terraform provider configuration

\* Terraform validation

\* Terraform execution plan

\* Terraform apply

\* AWS IAM user creation

\* Terraform state management

\* Terraform provider lock file

\* Troubleshooting duplicate configurations



\## 💻 Commands Practiced



```bash

terraform init

terraform validate

terraform plan

terraform apply

terraform destroy

```



\## 🚀 Terraform Workflow



The basic Terraform workflow practiced today was:



```text

Write Configuration

&#x20;      ↓

terraform init

&#x20;      ↓

terraform validate

&#x20;      ↓

terraform plan

&#x20;      ↓

terraform apply

&#x20;      ↓

AWS Resource Created

```



\## ☁️ AWS IAM Resource



Created an IAM user using Terraform:



```text

IAM User: sjcedemo

Purpose: hands-on

```



Terraform reported:



```text

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.

```



\## 📄 Terraform Files



The practice included Terraform configuration files such as:



```text

terraformpractise/

├── iam.tf

├── provider.tf

└── .terraform.lock.hcl

```



The `.terraform.lock.hcl` file records the selected provider version so Terraform can consistently use the same provider.



\## 🔍 Troubleshooting



After successfully creating the IAM user, Terraform reported duplicate configuration errors.



\### Error 1 – Duplicate Provider



```text

Error: Duplicate provider configuration

```



This occurred because the AWS provider was defined more than once.



\### Error 2 – Duplicate Resource



```text

Error: Duplicate resource "aws\_iam\_user" configuration

```



The same resource:



```text

aws\_iam\_user.demouser1

```



was declared in multiple `.tf` files.



\### Lesson Learned



Terraform loads \*\*all `.tf` files in the same directory as one configuration\*\*. Therefore:



\* Provider configurations should not be duplicated.

\* Resource names must be unique within a Terraform module.

\* Multiple `.tf` files are combined automatically by Terraform.



\## 🎯 Key Learning



Today I learned how Terraform can be used to manage AWS infrastructure using \*\*Infrastructure as Code\*\* instead of manually creating resources through the AWS Console.



I also learned how to identify and fix Terraform configuration errors involving duplicate providers and duplicate resources.



\## ✅ Result



Successfully:



\* Initialized Terraform

\* Installed the AWS provider

\* Validated the configuration

\* Generated a Terraform plan

\* Applied the configuration

\* Created an AWS IAM user

\* Identified duplicate provider/resource configuration errors



\## 📈 Skills Practiced



`Terraform` `AWS` `IAM` `IaC` `Terraform Provider` `terraform init` `terraform validate` `terraform plan` `terraform apply` `GitHub`



