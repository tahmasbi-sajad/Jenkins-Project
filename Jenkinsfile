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
                // دستور دپلوی واقعی مثل Docker Push یا K8s Apply
            }
        }
    }
    post {
        failure {
            mail to: 'tahmasbi.s92@gmail.com',
                 subject: "Pipeline Failed: ${currentBuild.fullDisplayName}",
                 body: "Check Jenkins console output for details: ${env.BUILD_URL}"
        }
    }
}

