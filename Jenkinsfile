pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Building the Node.js app"
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo "Running tests (if any)"
            }
        }
        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo "Deploying the app"
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
