# Day 61 -- Introduction to Terraform and Your First AWS Infrastructure

### Task 1: Understand Infrastructure as Code
Before touching the terminal, research and write short notes on:

1. What is Infrastructure as Code (IaC)? Why does it matter in DevOps?
   - Iac is DevOps practice where infrastructure- such as server , network , db & load balancers are provisioned & managed through code rather than manual processes
   - ensure consistency, repeatability & automation
   - In modern DevOps, it is a foundatiion of contionous delivery enabling teams to manage infrastructure
   - this result faster, safer & more reliable software delivery
     
2. What problems does IaC solve compared to manually creating resources in the AWS console?
   - Iac reduce the costs of developing software by eliminating the need if manual environment
   - Iac provides a constistant & repetable approch to cloud infrastructure management, reducing the risk of human error
     
3. How is Terraform different from AWS CloudFormation, Ansible, and Pulumi?
   - AWS Cloduformation is used for Iac in AWS , not in GCP or Azure platforms for while we can use Terraform for Iac inside or outside AWS
   - Ansible is a configuration tool and support mutable infrastructure, while terraform is provisioning tool , support immuyable infrastructure
   - pulumi is ideal when you need more flexibility or want to integrate infrastructure with application logic
   - while terraform s great for straightforward, declarative infrastructure setups.
     
4. What does it mean that Terraform is "declarative" and "cloud-agnostic"?
   ** declarative**
      - Terraform is declarative because you only write what you want the final infrastructure to look like (like servers, networks, etc.).
      - Terraform automatically figures out how to create or update it to match that desired state.
  
   ** cloud-agnostic**
     - terraform work with any cloud provider including AWS, GCP ,Azure etc..
     - it uses provider plugin to translate terraform code into API calls for specific platforms

---

### Task 2: Install Terraform and Configure AWS
1. Install Terraform:
```bash
# Linux (amd64)
wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform4
```
2. Verify:
```bash
terraform -version
```

3. Install and configure the AWS CLI:
```bash
aws configure
# Enter your Access Key ID, Secret Access Key, default region (e.g., ap-south-1), output format (json)
```

4. Verify AWS access:
```bash
aws sts get-caller-identity
```
