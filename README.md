# Automating Magento eCommerce Deployment on AWS Using Terraform and Ansible

<p align="center">
<img src="https://i.imgur.com/IZjOGKn.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

## Project Description
This project focuses on automating the deployment of a Magento-based eCommerce website on AWS using Ansible. Magento is a widely-used open-source platform for building eCommerce websites, but its deployment can be time-consuming and error-prone if done manually. In this project, automation is key to ensure that every aspect, from server provisioning to database configuration and website setup, is completed in a fully automated manner using Ansible playbooks. This process eliminates manual intervention, enhances consistency, and reduces the risk of errors.

Ansible is used to orchestrate the deployment, including configuring EC2 instances, installing necessary software such as Apache and MySQL, setting up the Magento application, and configuring caching and database services.

## Project Objectives
1. Automate the setup of a Magento eCommerce website on AWS using Ansible playbooks.
2. Ensure all components—web server, database, and caching—are fully automated.
3. Implement caching and database configurations to optimize website performance.
4. Reduce manual intervention in setting up users, databases, and Magento configurations.
5. Provide an efficient and scalable infrastructure that can be replicated easily for future deployments.

## Project Solution

### Phase 1: Infrastructure Provisioning with Terraform
1. **AWS Infrastructure Setup**: Terraform was used to define and provision the necessary AWS resources for hosting Magento. This included:
   - **VPC (Virtual Private Cloud)**: A custom VPC was created to isolate the Magento application for enhanced security.
   - **EC2 Instances**: Terraform provisioned multiple EC2 instances for the Magento application server and additional instances for backend services.
   - **RDS (MySQL) Database**: A managed RDS instance was provisioned for the Magento database, providing reliable and scalable storage.
   - **Elastic Load Balancer (ELB)**: The Elastic Load Balancer was configured to distribute traffic evenly across the EC2 instances, ensuring high availability.
   - **Auto Scaling Groups**: Terraform configured auto-scaling groups to automatically adjust the number of EC2 instances based on traffic demands.

2. **Networking and Security**:
   - **Security Groups**: Security groups were configured to allow access to the necessary ports, ensuring the system is secure from unauthorized access.
   - **Subnets and Routing**: Public and private subnets were created for different tiers of the application. Route tables were set up for internet access and inter-tier communication.
   - **Elastic IPs**: Elastic IPs were assigned to ensure persistent access to the instances and load balancer.

3. **Automation with Infrastructure-as-Code (IaC)**: Using Terraform's declarative syntax, the entire infrastructure was codified. This not only automated the provisioning process but also allowed for version control and repeatable deployments across environments (e.g., dev, staging, production). Terraform was integrated with a CI/CD pipeline to automatically deploy infrastructure changes.

### Phase 2: Configuration Management with Ansible
1. **Magento Application Installation**: After the infrastructure was provisioned, Ansible was used to automate the installation and configuration of the Magento application on the EC2 instances. The playbooks included tasks for:
   - Installing necessary dependencies such as PHP, MySQL, and Redis.
   - Configuring the Magento environment to optimize performance and security.
   - Deploying the Magento codebase to the EC2 instances.
   - Setting up the database connection to the RDS MySQL instance.

2. **Ansible for Continuous Configuration**: Ansible was also employed to manage ongoing configuration tasks and ensure the infrastructure was kept in the desired state. This included:
   - Automated backups and updates for the Magento system.
   - Automated scaling configuration for adding/removing instances based on demand.
   - Performance tuning by optimizing cache settings, database configurations, and system resources.

3. **Monitoring and Logging**: AWS CloudWatch was configured to monitor EC2 instances, load balancers, and RDS performance. Additionally, Ansible playbooks were used to configure logging and monitoring tools, ensuring that system administrators could track system health and detect any potential issues.

## Results
This solution enabled the fully automated, scalable deployment of Magento on AWS, significantly reducing manual effort and minimizing the risk of human error. The combination of Terraform for provisioning and Ansible for configuration management ensured that the infrastructure and application were consistently deployed across multiple environments. This approach provided high availability, enhanced performance, and simplified ongoing maintenance for the Magento eCommerce platform.

## Tools and Technologies
- **Amazon Web Services (AWS)**: EC2, S3, RDS
- **Ansible**: Automation and configuration management
- **MySQL**: Database for storing Magento data
- **Magento**: Open-source eCommerce platform
- **Apache HTTP Server**: Web server
- **Redis**: Caching system for performance enhancement
- **SSH**: Secure connection for EC2 instances
- **Linux**: Operating system for servers
- **PHP**: Programming language for Magento
- **Git**: Version control for managing Ansible playbooks

## Step-by-Step Directions

### Phase 1: Magento Setup and AWS Infrastructure Provisioning
1. **Create a Magento Free Account**:
   - Visit Magento Marketplace and create a free account. It May redirect you to https://commercemarketplace.adobe.com/

<p align="center">
<img src="https://i.imgur.com/dUBcF0j.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Create and Save the Public and Private Key from your Magento account Set Up Terraform for AWS Infrastructure Provisioning

<p align="center">
<img src="https://i.imgur.com/NKdgchs.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Install Terraform: Install Terraform on AWS Cloud Shell 

<p align="center">
<img src="https://i.imgur.com/dpTlcII.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/TRlWT8O.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Download the Terraform files: Make final_project Directory and Download the on AWS Cloud Shell

<p align="center">
<img src="https://i.imgur.com/5toWx3V.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/R0tVGIN.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/oqq8YWr.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Update Main.tf file: Update Main.tf file and Change VPC_ID to Default from your AWS default VPC.

<p align="center">
<img src="https://i.imgur.com/Q4KLLze.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Create an AWS IAM User: Set up an AWS IAM user with the necessary permissions (EC2, RDS, S3, VPC, and CloudWatch).

<p align="center">
<img src="https://i.imgur.com/V2uP5t5.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Configure AWS CLI: Set up your AWS CLI by running aws configure and entering the Access Key and Secret Key for the IAM user.

<p align="center">
<img src="https://i.imgur.com/oXNGr8M.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

2. **Run Terraform Scripts**:
   - Initialize Terraform by running terraform init in the directory where your configuration files are stored.

<p align="center">
<img src="https://i.imgur.com/gVjcanA.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Apply the configuration by running terraform apply to provision the AWS infrastructure. This will create the VPC, EC2 instances, RDS, and other necessary resources.

<p align="center">
<img src="https://i.imgur.com/fJuXMBH.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/SxgsgA6.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

### Install and Open Git Bash: To Remote into EC2 Server
1. Install Git Bash (if not already installed) from git-scm.com.
2. Open Git Bash on your local machine.

### Step 2: Clone the Repository
1. **Navigate to Your Project Directory**:
   - Use cd to move to the directory where you want to store the project files.

<p align="center">
<img src="https://i.imgur.com/DXvTG8b.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/CKJWsqH.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

### Phase 2: Configuration Management with Ansible
5. **Install and Configure Ansible**:
   - Install Ansible: Install Ansible on your local machine.

<p align="center">
<img src="https://i.imgur.com/pb39M8E.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Create Ansible Playbooks: Write Ansible playbooks to automate the configuration of the Magento application on the EC2 instances. The playbooks should include tasks to:
     - Install PHP, Nginx, and other Magento dependencies.
     - Configure the Magento application.
     - Deploy the Magento codebase from the downloaded files.
     - Set up database connection details for the RDS instance.

<p align="center">
<img src="https://i.imgur.com/a28Ftbm.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/uMwlREv.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

6. **Use Ansible for Application Deployment**:
   - Use the Ansible playbooks to install and configure Magento on the EC2 instances. Run the playbooks using ansible-playbook commands, ensuring that all tasks are executed in the correct order.

<p align="center">
<img src="https://i.imgur.com/EDbdtnR.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Verify that Magento is properly installed and configured by accessing the application via URL.

<p align="center">
<img src="https://i.imgur.com/T07NJwc.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/LVAD2tt.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

7. **Login and Edit Site**: 
   - Customize your E-commerce Site Add Products 

<p align="center">
<img src="https://i.imgur.com/y0zXc5l.jpeg" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Add Product to Cart

<p align="center">
<img src="https://i.imgur.com/rBmDVHj.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

After testing and completing the project, destroy the infrastructure by running terraform destroy to avoid unnecessary charges.

## Project Conclusion
The Terraform-based deployment successfully automated the provisioning and management of AWS infrastructure, meeting the project's scalability, security, and cost-efficiency objectives. By using Terraform, the setup was consistent and repeatable, which allowed for rapid deployment and simplified updates to the infrastructure. The use of Git for version control ensured that any changes were tracked and could be easily rolled back if necessary.

## Challenges Encountered
- **Resource Limits**: Encountered issues with AWS service limits (e.g., EC2 instance limits) that required adjusting the configurations and understanding AWS limitations.
- **Invalid VPC ID Error**: Received an error due to a malformed VPC ID, which was resolved by verifying VPC IDs and ensuring configuration accuracy.
- **Disk Space Issues**: Limited space on the development environment caused interruptions during deployment, leading to file cleanup and workspace management solutions.

## Lessons Learned
- **Importance of State Management**: Proper state management in Terraform is crucial for accurate tracking of resources, especially in complex projects.
- **Cloud Cost Awareness**: Understanding AWS's pricing structure is essential for cost-effective infrastructure management, particularly with scalable resources.
- **Configuration Validation**: Checking syntax and values in .tf files prevented errors and ensured smoother deployment.

## Future Improvements
- **Implement CI/CD Pipeline**: Integrate a CI/CD pipeline to automate the plan, apply, and destroy steps in a controlled environment.
- **Enhanced Monitoring and Logging**: Incorporate AWS CloudWatch and AWS Config for real-time monitoring and logging, enhancing observability and debugging capabilities.
- **Optimize Resource Scaling**: Investigate further optimizations for Auto Scaling groups to ensure high performance during peak traffic while minimizing costs.
