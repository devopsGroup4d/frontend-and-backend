# Project 1: Automated Deployment Pipeline with Jenkins and Docker - DevOps Engineer

This README file outlines the commands and steps used throughout the implementation of an automated CI/CD pipeline using Jenkins, Docker, and Ansible for the "Project 1: Automated Deployment Pipeline with Jenkins and Docker" as described.

## Week 1: Initial Setup & Planning

### 1. Install Jenkins and Docker:

**Local Environment (Example - Ubuntu):**

**Jenkins:**

```bash
# Add the Jenkins repository key
wget -O /var/run/jenkins/debian-installer/jenkins.io-2023.key [https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key](https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key)
sudo apt-key add /var/run/jenkins/debian-installer/jenkins.io-2023.key

# Add the Jenkins repository to your sources list
echo deb [signed-by=/var/run/jenkins/debian-installer/jenkins.io-2023.key] [https://pkg.jenkins.io/debian-stable](https://pkg.jenkins.io/debian-stable) binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list

# Update package lists and install Jenkins
sudo apt update
sudo apt install jenkins

# Start and enable Jenkins service
sudo systemctl start jenkins
sudo systemctl enable jenkins

# Check Jenkins status
sudo systemctl status jenkins

# Uninstall old versions (if any)
sudo apt-get remove docker docker-engine docker.io containerd runc

# Update the apt package index
sudo apt update

# Install prerequisites
sudo apt-get install -y apt-transport-https ca-certificates curl gnupg lsb-release

# Add Docker's official GPG key
curl -fsSL [https://download.docker.com/linux/ubuntu/gpg](https://download.docker.com/linux/ubuntu/gpg) | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Update the apt package index again
sudo apt update

# Install Docker Engine
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Start and enable Docker service
sudo systemctl start docker
sudo systemctl enable docker

# Verify Docker installation
docker --version
sudo systemctl status docker

sudo apt update
sudo apt install software-properties-common -y
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install ansible -y

# Verify Ansible installation
ansible --version

#Kubernetes commands
kubectl apply -f deployment.yaml: Apply the deployment manifest.
kubectl apply -f service.yaml: Apply the service manifest.
kubectl get deployments: Check deployment status.
kubectl get services: Check service status and external IP.
kubectl get pods: List running pods.