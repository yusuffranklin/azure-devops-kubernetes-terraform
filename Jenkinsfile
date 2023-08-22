pipeline{
    agent any
    options{
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    environment{
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    }

    stages{
        stage('Build Docker Image'){
            steps{
                sh 'sudo docker build -t yusuffranklin/currency-exchange-devops .'
            }
        }
        stage('Login'){
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push Docker Image'){
            steps{
                sh 'sudo docker push yusuffranklin/currency-exchange-devops'
            }
        }
    }
}