pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('benfadhel_4')
    }
    stages { 
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/benfadhel/docker-pipeline.git'
            }
        }

        stage('Build docker image') {
            steps {  
                sh 'docker build -t benfadhel/alpine_docker_waael .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login --username benfadhel --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh ' docker push benfadhel/alpine_docker_waael'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
