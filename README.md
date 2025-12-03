<<<<<<< HEAD
# Static-webSite-for-AWS-EC2-Terraform-Jenkins-GitHub-Webhook

##  Overview

This project demonstrates how to deploy a static website on AWS EC2 using Terraform and automate continuous delivery using Jenkins CI/CD pipeline triggered by GitHub Webhooks.

The solution ensures:

* Zero-touch automated deployment

* Infrastructure-as-Code provisioning

* Secure SSH-based code delivery

* Fully automated updates on every GitHub commit

##  Architecture Diagram

![](./Img/static%201.png)

##  Project Goals

* Deploy a static website using Terraform

* Configure EC2, security groups, and user-data automation

* Set up Jenkins for continuous deployment

* Enable GitHub → Jenkins pipeline trigger

* Auto-update the website after every commit

##  Repository Structure
```
static-web-deployment-terraform-jenkins/
│
├── main.tf
├── variables.tf
├── outputs.tf
├── terraform.tfvars
│
├── jenkinsfile
│
├── index.html
├── styles.css
├── about.html
├── blog.html
│
└── README.md
```
## (Changes Done)

✔ Terraform files moved under a clean `terraform`/ directory
✔ Jenkinsfile placed under `jenkins`/
✔ Website files grouped under `website`/
✔ Much more production-ready repo layout
##  Tools & Technologies

| Tool                | Purpose                     |
| ------------------- | --------------------------- |
| **Terraform**       | Infrastructure provisioning |
| **ubuntu**          | operating static website    |
| **AWS EC2**         | Website hosting             |
| **ssh key**         | Secure connection between   |    Jenkins and EC2
| **Nginx**           | Web server                  |
| **GitHub**          | Source code                 |
| **Jenkins**         | CI/CD automation            |
| **GitHub Webhooks** | Auto-trigger pipeline       |

##  Terraform Infrastructure
### ✔ EC2 Instance Setup
Terraform Infrastructure
✔ EC2 Instance

* Ubuntu 22.04 LTS AMI

* t2.micro instance

### Security Group:

* Allow Port 80 → Anywhere

* Allow Port 22 → your IP only (Secure!)

* User Data:

     * Installs: nginx
     * git
     * Clone repo `/var/www/html`

![](./Img/static2.png)  

### ✔ User Data Script (Auto Deployment)
```
#!/bin/bash
set -e

apt update -y
apt install -y nginx git

systemctl enable nginx
systemctl start nginx

git clone https://github.com/YOUR-REPO/static-website.git /var/www/html

chown -R www-data:www-data /var/www/html
chmod -R 755 /var/www/html

systemctl restart nginx
```
### Changes Done

✔ Corrected GitHub repo URL
✔ Corrected folder structures
✔ Standardized permissions

###  Jenkins CI/CD Pipeline

#### Jenkins CI/CD Pipeline

* 1 Checkout SCM

* 2 SSH into EC2

* 3 Pull latest code

* 4 Replace website content

* 5 Deploy Code 

* 6 Smoke Test 

* 7 Restart nginx 


### Jenkinsfile (Pipeline Script)
```python
pipeline {
    agent any

    stages {
        stage('Pull Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/mansikadam1100/Static-webSite-for-AWS-EC2-Terraform-Jenkins-GitHub-Webhook'
            }
        }

        stage('SSH into EC2 & Update Website') {
            steps {
                sshagent(['ubuntu']) {
                    sh '''
                    ssh -o StrictHostKeyChecking=no ec2-user@15.207.111.25 "sudo rm -rf /var/www/html/*"
                    ssh ec2-user@15.207.111.25 "sudo git clone https://github.com/rutikakale/Static-Site-on-AWS-EC2-Terraform-Jenkins-GitHub-Webhook.git /var/www/html"
                    ssh ec2-user@15.207.111.25 "sudo systemctl restart nginx"
                    '''
                }
            }
        }
    }
}
```

###  Deployment Steps
#### 1️⃣ Deploy Infrastructure (Terraform)
```
cd terraform
terraform init
terraform plan
terraform apply -auto-approve
```
#### 2️⃣ Setup Jenkins
* Install Jenkins + plugins

* Create pipeline job

* add ssh key credential -> deploy-ssh-key

* Add SSH private key

* set GitHub Webhook

http://12.476.876.72/github-webhook/
![](./Img/static4.png)

#### 3️⃣ Auto Deployment
* Developer pushes code 

*  Github Webhook triggers Jenkins

* Jenkins deploys changes to EC2

* Nginx restarts

* Website instantly updates

###  Validation Checklist

* Website loads through EC2 Public IP

* Jenkins pipeline runs successfully

* `/var/www/html` contains latest code

* GitHub commit instantly reflects on server 

###  Screenshots (Evidence)

-**Successful static website deployment** on AWS EC2

![](./Img/static3.png)
---
-**Fully automated CI/CD pipeline** using Jenkins

![](./Img/Cicd%20pipeline%20success.png)
---

![](./Img/static4.png)
---
###  Final Results

* Static website deployed successfully

* Fully automated CI/CD pipeline

* Terraform → Jenkins → GitHub integration working

* Cleaner repo structure

* Secure deployment

* Zero manual steps required

This project delivers a complete DevOps automation pipeline using Terraform + Jenkins, ensuring reliable, repeatable, and fully automated website deployments.

=======
# Static-webSite-for-AWS-EC2-Terraform-Jenkins-GitHub-Webhook

##  Overview

This project demonstrates how to deploy a static website on AWS EC2 using Terraform and automate continuous delivery using Jenkins CI/CD pipeline triggered by GitHub Webhooks.

The solution ensures:

* Zero-touch automated deployment

* Infrastructure-as-Code provisioning

* Secure SSH-based code delivery

* Fully automated updates on every GitHub commit

##  Architecture Diagram

![](./Img/static%201.png)

##  Project Goals

* Deploy a static website using Terraform

* Configure EC2, security groups, and user-data automation

* Set up Jenkins for continuous deployment

* Enable GitHub → Jenkins pipeline trigger

* Auto-update the website after every commit

##  Repository Structure
```
static-web-deployment-terraform-jenkins/
│
├── main.tf
├── variables.tf
├── outputs.tf
├── terraform.tfvars
│
├── jenkinsfile
│
├── index.html
├── styles.css
├── about.html
├── blog.html
│
└── README.md
```
## (Changes Done)

✔ Terraform files moved under a clean `terraform`/ directory
✔ Jenkinsfile placed under `jenkins`/
✔ Website files grouped under `website`/
✔ Much more production-ready repo layout
##  Tools & Technologies

| Tool                | Purpose                     |
| ------------------- | --------------------------- |
| **Terraform**       | Infrastructure provisioning |
| **ubuntu**          | operating static website    |
| **AWS EC2**         | Website hosting             |
| **ssh key**         | Secure connection between   |    Jenkins and EC2
| **Nginx**           | Web server                  |
| **GitHub**          | Source code                 |
| **Jenkins**         | CI/CD automation            |
| **GitHub Webhooks** | Auto-trigger pipeline       |

##  Terraform Infrastructure
### ✔ EC2 Instance Setup
Terraform Infrastructure
✔ EC2 Instance

* Ubuntu 22.04 LTS AMI

* t2.micro instance

### Security Group:

* Allow Port 80 → Anywhere

* Allow Port 22 → your IP only (Secure!)

* User Data:

     * Installs: nginx
     * git
     * Clone repo `/var/www/html`

![](./Img/static2.png)  

### ✔ User Data Script (Auto Deployment)
```
#!/bin/bash
set -e

apt update -y
apt install -y nginx git

systemctl enable nginx
systemctl start nginx

git clone https://github.com/YOUR-REPO/static-website.git /var/www/html

chown -R www-data:www-data /var/www/html
chmod -R 755 /var/www/html

systemctl restart nginx
```
### Changes Done

✔ Corrected GitHub repo URL
✔ Corrected folder structures
✔ Standardized permissions

###  Jenkins CI/CD Pipeline

#### Jenkins CI/CD Pipeline

* 1 Checkout SCM

* 2 SSH into EC2

* 3 Pull latest code

* 4 Replace website content

* 5 Deploy Code 

* 6 Smoke Test 

* 7 Restart nginx 


### Jenkinsfile (Pipeline Script)
```python
pipeline {
    agent any

    stages {
        stage('Pull Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/mansikadam1100/Static-webSite-for-AWS-EC2-Terraform-Jenkins-GitHub-Webhook'
            }
        }

        stage('SSH into EC2 & Update Website') {
            steps {
                sshagent(['ubuntu']) {
                    sh '''
                    ssh -o StrictHostKeyChecking=no ec2-user@15.207.111.25 "sudo rm -rf /var/www/html/*"
                    ssh ec2-user@15.207.111.25 "sudo git clone https://github.com/rutikakale/Static-Site-on-AWS-EC2-Terraform-Jenkins-GitHub-Webhook.git /var/www/html"
                    ssh ec2-user@15.207.111.25 "sudo systemctl restart nginx"
                    '''
                }
            }
        }
    }
}
```

###  Deployment Steps
#### 1️⃣ Deploy Infrastructure (Terraform)
```
cd terraform
terraform init
terraform plan
terraform apply -auto-approve
```
#### 2️⃣ Setup Jenkins
* Install Jenkins + plugins

* Create pipeline job

* add ssh key credential -> deploy-ssh-key

* Add SSH private key

* set GitHub Webhook

http://12.476.876.72/github-webhook/
![](./Img/static4.png)

#### 3️⃣ Auto Deployment
* Developer pushes code 

*  Github Webhook triggers Jenkins

* Jenkins deploys changes to EC2

* Nginx restarts

* Website instantly updates

###  Validation Checklist

* Website loads through EC2 Public IP

* Jenkins pipeline runs successfully

* `/var/www/html` contains latest code

* GitHub commit instantly reflects on server 

###  Screenshots (Evidence)

-**Successful static website deployment** on AWS EC2

![](./Img/static3.png)
---
-**Fully automated CI/CD pipeline** using Jenkins

![](./Img/Cicd%20pipeline%20success.png)
---

![](./Img/static4.png)
---
###  Final Results

* Static website deployed successfully

* Fully automated CI/CD pipeline

* Terraform → Jenkins → GitHub integration working

* Cleaner repo structure

* Secure deployment

* Zero manual steps required

This project delivers a complete DevOps automation pipeline using Terraform + Jenkins, ensuring reliable, repeatable, and fully automated website deployments.

>>>>>>> 19e0491f3a6384bb7f408bd8372aae0549b86ba0
