pipeline {
    agent any

    environment {
        IMAGE_NAME = 'lixweb/demo-app'
        CONTAINER_NAME = 'demo-app'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/lixweb/demo-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ${IMAGE_NAME} .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker rm -f ${CONTAINER_NAME} || true'
                sh 'docker run -d -p 9090:80 --name ${CONTAINER_NAME} ${IMAGE_NAME}'
            }
        }
    }
}

