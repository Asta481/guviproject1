pipeline {
    agent any
    environment {
        DOCKER_HUB_CREDENTIALS = credentials('docker-hub') // Docker Hub credentials in Jenkins
        DOCKER_USERNAME = 'priyadharshan481'
        DEV_REPO = 'test'
        PROD_REPO = 'dev'
    }
    stages {
        stage('Clone Repository') {
            steps {
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'test') {
                        sh "docker build -t  priyadharshan481/test:latest ."
                    } else if (env.BRANCH_NAME == 'dev') {
                        sh "docker build -t  priyadharshan481/dev:latest ."
                    }
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    sh "echo ${DOCKER_HUB_CREDENTIALS_PSW} | docker login -u  priyadharshan481 --Asta.@4810-stdin"
                    if (env.BRANCH_NAME == 'test') {
                        sh "docker push  priyadharshan481/test:latest"
                    } else if (env.BRANCH_NAME == 'dev') {
                        sh "docker push  priyadharshan481/dev:latest"
                    }
                }
            }
        }
    }
}
