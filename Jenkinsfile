pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('test1')
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh 'docker build -t gunaxpds/flaskapp:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push gunaxpds/flaskapp:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
