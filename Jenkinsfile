pipeline {
    agent { label 'linux' }
    environment {
        DOCKERHUB_CREDENTIALS= credentials('docker-hub')
    }
    stages {

        stage('Build') {
            steps {
                sh 'docker build -t zakhar0kostyshyn/jenkins-alpine-example:latest .'
            }
        }

        stage('Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }

        stage('Push') {
            steps {
                sh 'docker push zakhar0kostyshyn/jenkins-alpine-example:latest'
            }
        }

    }

    post {
        always {
            sh 'docker logout'
        }
    }

}