# DevSecOps Project

## Phase 1: Initial Setup and Deployment

### Step 1: Launch EC2 (Ubuntu 22.04)

# Provision an EC2 instance on AWS with Ubuntu 22.04.
# Connect to the instance using SSH.

### Step 2: Clone the Code

# Update all the packages and then clone the code.
# Clone your application's code repository onto the EC2 instance:

git clone https://github.com/N4si/DevSecOps-Project.git

### Step 3: Install Docker and Run the App Using a Container

# Set up Docker on the EC2 instance:

sudo apt-get update
sudo apt-get install docker.io -y
sudo usermod -aG docker $USER  # Replace with your system's username, e.g., 'ubuntu'
newgrp docker
sudo chmod 777 /var/run/docker.sock

# Build and run your application using Docker containers:

docker build -t netflix .
docker run -d --name netflix -p 8081:80 netflix:latest

#### To Delete:

docker stop <containerid>
docker rmi -f netflix

# It will show an error because you need an API key.

### Step 4: Get the API Key

# Open a web browser and navigate to TMDB (The Movie Database) website.
# Click on "Login" and create an account.
# Once logged in, go to your profile and select "Settings."
# Click on "API" from the left-side panel.
# Create a new API key by clicking "Create" and accepting the terms and conditions.
# Provide the required basic details and click "Submit."
# You will receive your TMDB API key.
# Now recreate the Docker image with your API key:

docker build --build-arg TMDB_V3_API_KEY=<your-api-key> -t netflix .

## Phase 2: Security

### Install SonarQube and Trivy

# Install SonarQube and Trivy on the EC2 instance to scan for vulnerabilities.

#### SonarQube

docker run -d --name sonar -p 9000:9000 sonarqube:lts-community

# To access:

# publicIP:9000 (by default username & password is admin)

#### Install Trivy

sudo apt-get install wget apt-transport-https gnupg lsb-release
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -
echo deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt-get update
sudo apt-get install trivy

# To scan an image using Trivy:

trivy image <imageid>

### Integrate SonarQube and Configure

# Integrate SonarQube with your CI/CD pipeline.
# Configure SonarQube to analyze code for quality and security issues.

## Phase 3: CI/CD Setup

### Install Jenkins for Automation

# Install Jenkins on the EC2 instance to automate deployment.

#### Install Java

sudo apt update
sudo apt install fontconfig openjdk-17-jre
java -version

# Output:
# openjdk version "17.0.8" 2023-07-18
# OpenJDK Runtime Environment (build 17.0.8+7-Debian-1deb12u1)
# OpenJDK 64-Bit Server VM (build 17.0.8+7-Debian-1deb12u1, mixed mode, sharing)

#### Jenkins Installation

sudo wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
sudo systemctl start jenkins
sudo systemctl enable jenkins

# Access Jenkins in a web browser using the public IP of your EC2 instance:

# publicIp:8080

#### Install Necessary Plugins in Jenkins

# Go to Manage Jenkins → Plugins → Available Plugins → Install the following plugins:

# 1. Eclipse Temurin Installer (Install without restart)
# 2. SonarQube Scanner (Install without restart)
# 3. NodeJs Plugin (Install Without restart)
# 4. Email Extension Plugin

# Configure Java and Nodejs in Global Tool Configuration:

# Go to Manage Jenkins → Tools → Install JDK (17) and NodeJs (16) → Click Apply and Save.

#### Configure SonarQube in Jenkins

# Create the token.
# Go to Jenkins Dashboard → Manage Jenkins → Credentials → Add Secret Text. It should look like this.
# After adding sonar token, click Apply and Save.
