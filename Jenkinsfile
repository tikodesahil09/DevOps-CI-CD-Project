pipeline {
    agent any

    stages {

        stage('Git Clone') {
            steps {
                git url: 'https://github.com/tikodesahil09/DevOps-Workflow-Webpage.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-website .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop my-container || true
                docker rm my-container || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 80:80 --name my-container my-website'
            }
        }
    }

    post {
        success {
            echo "===== Docker Deployment Successful ====="
        }
        failure {
            echo "===== Deployment Failed ====="
        }
    }
}
