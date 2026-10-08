\# Day 7 – Terraform \& AWS IAM, EC2 and VPC Practice



\## 📅 Date



5 October 2026



\## 📌 Overview



Today I practiced \*\*Terraform with AWS\*\* and learned how to use \*\*Infrastructure as Code (IaC)\*\* to create and manage AWS resources.



The practice covered \*\*AWS IAM, EC2, VPC, Subnet, Internet Gateway, Route Table, and AWS CLI\*\* using Terraform.



\## 🛠️ Tools Used



\* Terraform

\* AWS CLI

\* AWS IAM

\* AWS EC2

\* AWS VPC

\* Visual Studio Code

\* PowerShell

\* Git \& GitHub



\---



\## 1. Terraform Initialization



Initialized Terraform and downloaded the required AWS provider.



```powershell

terraform init

```



Terraform initialized the working directory and prepared it for AWS resource management.



\---



\## 2. Terraform Formatting and Validation



```powershell

terraform fmt

terraform validate

```



\### `terraform fmt`



Formats Terraform configuration files according to the standard Terraform style.



\### `terraform validate`



Checks whether the Terraform configuration is syntactically valid and internally consistent.



\---



\## 3. Terraform Plan



```powershell

terraform plan

```



The `terraform plan` command was used to preview the AWS resources that Terraform would create or modify.



\---



\## 4. Terraform Apply



```powershell

terraform apply

```



Terraform asked for confirmation before creating the resources.



```text

yes

```



After confirmation, Terraform created the configured AWS resources.



\---



\# ☁️ AWS IAM



\## 5. Create IAM User



Created an AWS IAM user using Terraform.



```hcl

resource "aws\_iam\_user" "demouser1" {

&#x20; name = "sjcedemo"

}

```



\### IAM User Details



```text

IAM User : sjcedemo

Purpose  : Hands-on Terraform practice

```



This demonstrated how AWS IAM resources can be managed using Infrastructure as Code.



\---



\# 🖥️ AWS EC2



\## 6. EC2 Configuration



Created an EC2 instance using Terraform.



```hcl

resource "aws\_instance" "demoinstance" {

&#x20; ami           = "ami-07f9c6534b9c70941"

&#x20; instance\_type = "t3.micro"

&#x20; key\_name      = "sjcedemo"



&#x20; tags = {

&#x20;   Name = "demoinstance"

&#x20; }

}

```



\### EC2 Configuration



```text

Region        : us-east-1

Instance Name : demoinstance

Instance Type : t3.micro

Key Pair      : sjcedemo

```



\---



\## 7. Check Free Tier Eligible Instance Types



Used AWS CLI to check instance types eligible for the account's current Free Tier rules.



```powershell

aws ec2 describe-instance-types --region us-east-1 --filters "Name=free-tier-eligible,Values=true" --query "InstanceTypes\[\*].InstanceType" --output table

```



This helped identify suitable EC2 instance types before deployment.



\---



\# 🌐 AWS VPC



\## 8. VPC Creation



Created a VPC using Terraform.



```text

VPC CIDR : 10.0.0.0/16

Region   : us-east-1

```



\### VPC Terraform Code



```hcl

resource "aws\_vpc" "demovpc" {

&#x20; cidr\_block = "10.0.0.0/16"



&#x20; tags = {

&#x20;   Name = "demo-vpc"

&#x20; }

}

```



\---



\## 9. Public Subnet



Created a public subnet inside the VPC.



```hcl

resource "aws\_subnet" "public\_subnet" {

&#x20; vpc\_id                  = aws\_vpc.demovpc.id

&#x20; cidr\_block              = "10.0.1.0/24"

&#x20; availability\_zone       = "us-east-1a"

&#x20; map\_public\_ip\_on\_launch = true



&#x20; tags = {

&#x20;   Name = "demo-public-subnet"

&#x20; }

}

```



\### Subnet Configuration



```text

VPC CIDR       : 10.0.0.0/16

Subnet CIDR    : 10.0.1.0/24

Availability   : us-east-1a

Type           : Public Subnet

```



\---



\## 10. Internet Gateway



Created an Internet Gateway and attached it to the VPC.



```hcl

resource "aws\_internet\_gateway" "igw" {

&#x20; vpc\_id = aws\_vpc.demovpc.id



&#x20; tags = {

&#x20;   Name = "demo-igw"

&#x20; }

}

```



The Internet Gateway provides a path for communication between the VPC and the internet.



\---



\## 11. Public Route Table



Created a public route table with an internet route.



```hcl

resource "aws\_route\_table" "public\_rt" {

&#x20; vpc\_id = aws\_vpc.demovpc.id



&#x20; route {

&#x20;   cidr\_block = "0.0.0.0/0"

&#x20;   gateway\_id = aws\_internet\_gateway.igw.id

&#x20; }



&#x20; tags = {

&#x20;   Name = "demo-public-route-table"

&#x20; }

}

```



The route:



```text

0.0.0.0/0 → Internet Gateway

```



allows internet-bound traffic to use the Internet Gateway.



\---



\## 12. Route Table Association



Associated the public subnet with the public route table.



```hcl

resource "aws\_route\_table\_association" "public\_association" {

&#x20; subnet\_id      = aws\_subnet.public\_subnet.id

&#x20; route\_table\_id = aws\_route\_table.public\_rt.id

}

```



\---



\# 📁 VPC Architecture



```text

&#x20;                        Internet

&#x20;                           |

&#x20;                    Internet Gateway

&#x20;                           |

&#x20;                  ┌─────────────────┐

&#x20;                  │     demo-vpc    │

&#x20;                  │   10.0.0.0/16   │

&#x20;                  │                 │

&#x20;                  │  Public Subnet  │

&#x20;                  │   10.0.1.0/24   │

&#x20;                  │        |        │

&#x20;                  │  EC2 Instance   │

&#x20;                  └─────────────────┘

```



\---



\# 🔧 Troubleshooting



\## Invalid AMI



Encountered:



```text

InvalidAMIID.NotFound

```



\### Solution



Used a valid AMI available in the `us-east-1` region.



\---



\## Extra Space in AMI



Encountered:



```text

InvalidAMIID.Malformed

```



Incorrect:



```hcl

ami = " ami-07f9c6534b9c70941"

```



Correct:



```hcl

ami = "ami-07f9c6534b9c70941"

```



The extra space before the AMI ID was removed.



\---



\## Missing Key Pair



Encountered:



```text

InvalidKeyPair.NotFound

```



\### Solution



Created/configured the required EC2 key pair:



```text

sjcedemo

```



\---



\## Free Tier Instance Type



AWS rejected an instance type because it was not eligible for the account's current Free Tier rules.



Used the following command to check eligible instance types:



```powershell

aws ec2 describe-instance-types --region us-east-1 --filters "Name=free-tier-eligible,Values=true" --query "InstanceTypes\[\*].InstanceType" --output table

```



\---



\# 📸 Screenshots



\## Terraform Code – EC2



\## Terraform Code – VPC



\## Terraform VPC Configuration



\---



\# 📚 Key Learning



Today I learned how to:



\* Use Terraform for AWS Infrastructure as Code

\* Initialize and configure the AWS provider

\* Format Terraform configuration

\* Validate Terraform configuration

\* Generate a Terraform execution plan

\* Apply Terraform configuration

\* Create an IAM user using Terraform

\* Configure an EC2 instance

\* Select a valid AMI

\* Configure an EC2 key pair

\* Check Free Tier eligible instance types

\* Create an AWS VPC

\* Create a public subnet

\* Create an Internet Gateway

\* Create a public route table

\* Associate a subnet with a route table

\* Troubleshoot AWS and Terraform errors



\---



\# 💻 Main Terraform Commands



```powershell

terraform init

terraform fmt

terraform validate

terraform plan

terraform apply

terraform destroy

```



\---



\# ☁️ AWS CLI Commands



\### Check EC2 Key Pairs



```powershell

aws ec2 describe-key-pairs --region us-east-1 --query "KeyPairs\[\*].KeyName" --output table

```



\### Check Free Tier Eligible Instance Types



```powershell

aws ec2 describe-instance-types --region us-east-1 --filters "Name=free-tier-eligible,Values=true" --query "InstanceTypes\[\*].InstanceType" --output table

```



\---



\# 🎯 Terraform Workflow



```text

Write Terraform Configuration

&#x20;           ↓

&#x20;     terraform init

&#x20;           ↓

&#x20;     terraform fmt

&#x20;           ↓

&#x20;     terraform validate

&#x20;           ↓

&#x20;     terraform plan

&#x20;           ↓

&#x20;     terraform apply

&#x20;           ↓

&#x20;     AWS Resources Created

```



\---



\# ✅ Result



Successfully practiced \*\*Terraform and AWS Infrastructure as Code\*\* by creating and configuring:



\* AWS IAM User

\* AWS EC2 Instance

\* AWS VPC

\* Public Subnet

\* Internet Gateway

\* Public Route Table

\* Route Table Association



I also practiced troubleshooting common Terraform and AWS errors related to \*\*AMI IDs, key pairs, instance types, and configuration\*\*.



\---



\## 🚀 Skills Practiced



`Terraform` `AWS` `IAM` `EC2` `VPC` `Subnet` `Internet Gateway` `Route Table` `AWS CLI` `IaC` `PowerShell` `GitHub`



