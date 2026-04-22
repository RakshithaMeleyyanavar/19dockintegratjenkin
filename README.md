# 19dockintegratjenkin IN STEP 03 ADD PIPELINE SCRPT IN JENKINS  



pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                echo "Cloning GitHub repo..."
                git 'https://github.com/RakshithaMeleyyanavar/19dockintegratjenkin.git'
            }
        }

        stage('Check Files') {
            steps {
                echo "Checking workspace files..."
                bat 'dir'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "Building Docker image..."
                bat 'docker build -t my-app .'
            }
        }

        stage('Run Container') {
            steps {
                echo "Running Docker container..."
                bat 'docker run -d my-app'
            }
        }
    }

    post {
        success {
            echo "PIPELINE SUCCESS ✅ Docker container running"
        }
        failure {
            echo "PIPELINE FAILED ❌ Check logs"
        }
    }
}






STEP 6: VERIFY DOCKER OUTPUT

Open CMD / Terminal:

✔ Check Docker Images
docker images


👉 You should see:

my-app

✔ Check Running Containers
docker ps


👉 You should see container running



docker images
docker ps
