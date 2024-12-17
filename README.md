# Production-Grade-ML-Project
## Overview

This repository showcases a machine learning project pipeline designed to predict [ Specific Outcome ]. It incorporates AWS EC2 for deployment, Docker for containerization, Evidently AI for model monitoring, MongoDB for database management, and GitHub Actions for CI/CD deployment. The project adheres to modular coding principles, ensuring scalability and maintainability.

## Features

* __Machine Learning Pipeline__: Includes data preprocessing, feature engineering, model training, and evaluation.
* __Deployment on AWS EC2__: Deployed the pipeline on an EC2 instance for seamless scalability and accessibility.
* __Containerization with Docker__: Used Docker to ensure portability and consistency across environments.
* __Monitoring with Evidently AI__: Integrated Evidently AI to track data drift, model performance, and other key metrics.
* __Database Integration__: Utilized MongoDB to store and manage processed data and predictions.
* __CI/CD with GitHub Actions__: Automated testing and deployment workflows for efficient updates.

## Technologies Used

* Python 3.8+
* Docker and Docker Compose
* AWS account with EC2 access
* MongoDB instance (local or cloud-based)
* GitHub repository linked to your project
## AWS EC2 Setup and Docker Installation

1. Launch an EC2 Instance

* Choose an Ubuntu AMI for the instance.
* Allow necessary ports (e.g., 22 for SSH, 80 for HTTP) in the security group.
* Connect to your instance using SSH:

<div>
    <pre>`ssh -i "your-key.pem" ubuntu@<EC2-IP-ADDRESS>`</pre>
</div>


2. Install Docker on EC2

<div>
    <pre>
`sudo apt-get update -y`
`sudo apt-get upgrade -y`
`curl -fsSL https://get.docker.com -o get-docker.sh`
`sudo sh get-docker.sh`
`sudo usermod -aG docker ubuntu`
`newgrp docker`
   </pre>
</div>

3. Set Environment Variables

<div>
    <pre>
    Export __MONGODB_URL__="mongodb+srv://<username>:<password>@cluster.mongodb.net/<dbname>?retryWrites=true&w=majority"
    Export __AWS_ACCESS_KEY_ID__=<AWS_ACCESS_KEY_ID>
    Export __AWS_SECRET_ACCESS_KEY__=<AWS_SECRET_ACCESS_KEY>  
    </pre>
</div>



4. Pull and Run Docker Containers

* Clone the repository:

<div>
    <pre>
    `git clone https://github.com/yourusername/DataFlow-Prediction-Pipeline.git`
    `cd DataFlow-Prediction-Pipeline`
    </pre>
</div>

* Build and run the container:

<div>
    <pre>docker-compose up --build -d</pre>
</div>


## Self-Hosted Runner Setup on EC2

1. Go to GitHub Repository Settings

<div>
    <pre>Navigate to Settings > Actions > Runners > New self-hosted runner.</pre>
</div>

2. Select OS and Run Commands

* Choose Linux and execute the provided commands one by one in your EC2 terminal:

<div>
    <pre>
mkdir actions-runner && cd actions-runner
curl -o actions-runner-linux-x64-2.309.0.tar.gz -L https://github.com/actions/runner/releases/download/v2.309.0/actions-runner-linux-x64-2.309.0.tar.gz
tar xzf ./actions-runner-linux-x64-2.309.0.tar.gz
./config.sh --url https://github.com/yourusername/DataFlow-Prediction-Pipeline --token YOUR_GITHUB_TOKEN
./run.sh</pre>
</div>


3. Set the Runner to Start Automatically

<div>
    <pre>
    sudo ./svc.sh install
sudo ./svc.sh start
    </pre>
</div>
\

## GitHub Secrets Setup

1. Go to Settings > Secrets and variables > Actions > New repository secret.

2. Add the following secrets:

* AWS_ACCESS_KEY_ID
* AWS_SECRET_ACCESS_KEY
* AWS_DEFAULT_REGION (e.g., us-east-1)
* ECR_REPO (for Docker images)


