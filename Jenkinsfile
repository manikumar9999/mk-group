
pipeline {
    agent any
    environment{
        DOCKERHUB_CREDENTIALS=credentials('docker-hub')
    }
    stages{
        stage('docker build'){
            steps{
                sh 'docker build -t manikumar99/srikanth:$BUILD_NUMBER .'
            }
        }
        stage('docker login'){
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('docker push'){
            steps{
                sh 'docker push manikumar99/srikanth:$BUILD_NUMBER'
            }
        }
    }
    post{
        always{
            sh 'docker logout'
        }
    }
}
