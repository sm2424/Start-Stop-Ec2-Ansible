# Start-Stop-Ec2-Ansible-Jenkins pipeline
Launch an Ubuntu(22.04) T2 medium Instance

# To Install Jenkins
  #!/bin/bash
  sudo apt update -y
  wget -O - https://packages.adoptium.net/artifactory/api/gpg/key/public | tee /etc/apt/keyrings/adoptium.asc
  echo "deb [signed-by=/etc/apt/keyrings/adoptium.asc] https://packages.adoptium.net/artifactory/deb $(awk -F= '/^VERSION_CODENAME/{print$2}' /etc/os-release) main" | tee /etc/apt/sources.list.d/adoptium.list
  sudo apt update -y
  sudo apt install temurin-17-jdk -y
  /usr/bin/java --version
  curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
                  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
  echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
                  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
                              /etc/apt/sources.list.d/jenkins.list > /dev/null
  sudo apt-get update -y
  sudo apt-get install jenkins -y
  sudo systemctl enable jenkins
  sudo systemctl restart jenkins

# <EC2 Public IP Address:8080>
  sudo cat /var/lib/jenkins/secrets/initialAdminPassword
----------------------------------------------------------------------------------------------------------------------------------------------
# Install Ansible and Python
Step1:Update your system packages.
    sudo apt-get update
    
Step 2: First Install Required packages to install Ansible.
    sudo apt install software-properties-common

Step3: Add the ansible repository via PPA.
    sudo add-apt-repository --yes --update ppa:ansible/ansible

# Install Python3 for Ansible
    sudo apt install python3
# Install Ansible 
    sudo apt install ansible -y
    sudo apt install ansible-core
    ansible --version
# Install Python-pip3:
    sudo apt install python3-pip -y
    (this is just comment -  Package manager for python)Install Boto Framework - AWS SDKsudo pip3 install boto boto3

# Install Boto Framework - AWS SDK
    sudo pip3 install boto boto3
# Ansible will access AWS resources using Boto SDK
    sudo apt-get install python3-boto -y
    pip list boto | grep boto

# let's create and attach an IAM role ec2 instance
    Create Roles
    ![image](https://github.com/sm2424/Start-Stop-Ec2-Ansible/assets/91906122/08a63bf7-065f-48df-b7a8-fd059ca9d1b5)
  
# Add permissions policies
  
    AmazonEC2FullAccess
  
    click Next

    Click the "Role name" field.

    Type "Jenkins-cicd"

    Click "Create role"

    Click "EC2"

# Go to the Jenkins instance and add this role to the Jenkins-Ec2 instance.
    => Select Jenkins instance --> Actions --> Security --> Modify IAM role
       Add a newly created Role and click on Update IAM role
       ![image](https://github.com/sm2424/Start-Stop-Ec2-Ansible/assets/91906122/09740b82-6213-44af-90e2-fc5f87cc671c)

------------------------------------------------------------------------------------------------------------------------
# Let's go to the Jenkins machine and add the Ansible Plugin

    => Manage Jenkins --> Plugins --> Available Plugins

    => search for Ansible and install

    ![image](https://github.com/sm2424/Start-Stop-Ec2-Ansible/assets/91906122/db61c508-767a-40e1-be8c-b0542d9085da)

# Give this command in your Jenkins machine to find the path of your ansible which is used in the tool section of Jenkins.
    which ansible

    Copy that path and add it to the tools section of Jenkins at ansible installations.
    
      ![image](https://github.com/sm2424/Start-Stop-Ec2-Ansible/assets/91906122/8116d26e-ec7c-43fa-a8aa-5a83d701709d)


















