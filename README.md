# 19dockintegratjenkin IN STEP 03 ADD PIPELINE SCRPT IN JENKINS  



pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                echo "Cloning GitHub repo..."
                git 'https://github.com/YOUR_USERNAME/Docker-Jenkins-Integration.git'
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
