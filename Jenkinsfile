pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "nodejsapp:latest"
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out source code from Git"
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "Building Docker image from Dockerfile"
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests (if any)"
                // در اینجا می‌توانی npm test اضافه کنی
            }
        }

        stage('Deploy') {
            when {
                branch 'master'
            }
            steps {
                echo "Deploying the Docker container"
                sh 'docker run -d -p 3000:3000 $DOCKER_IMAGE'
            }
        }
    }

    post {
        success {
            mail to: 'tahmasbi.sajad92@gmail.com',
                 subject: "Build SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Congratulations! Build SUCCESS for ${env.JOB_NAME}.\nCheck details at ${env.BUILD_URL}"
        }
        failure {
            mail to: 'tahmasbi.sajad92@gmail.com',
                 subject: "Build FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Oops! Build FAILED for ${env.JOB_NAME}.\nCheck details at ${env.BUILD_URL}"
        }
    }
}

