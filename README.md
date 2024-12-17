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

`ssh -i "your-key.pem" ubuntu@<EC2-IP-ADDRESS>`
2. Install Docker on EC2


sudo apt-get update -y
sudo apt-get upgrade -y
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker
3. Set Environment Variables


export MONGODB_URL="mongodb+srv://<username>:<password>@cluster.mongodb.net/<dbname>?retryWrites=true&w=majority"
export AWS_ACCESS_KEY_ID=<AWS_ACCESS_KEY_ID>
export AWS_SECRET_ACCESS_KEY=<AWS_SECRET_ACCESS_KEY>  # Optional
4. Pull and Run Docker Containers

* Clone the repository:

git clone https://github.com/yourusername/DataFlow-Prediction-Pipeline.git
cd DataFlow-Prediction-Pipeline
Build and run the container:

* docker-compose up --build -d

