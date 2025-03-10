pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'springbootdockerdemo2'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/harish1817v/config-repo'  // Use your actual repo URL
            }
        }

        stage('Build') {
            steps {
                sh './mvnw clean package'  // Use './mvnw' if Maven Wrapper is available
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t ${DOCKER_IMAGE} .'
            }
        }

        stage('Docker Compose Up') {
            steps {
                sh 'docker-compose up --build -d'
            }
        }
    }

    post {
        success {
            echo "Build and deployment successful!"
        }
        failure {
            echo "Build failed. Check the logs."
        }
    }
}
