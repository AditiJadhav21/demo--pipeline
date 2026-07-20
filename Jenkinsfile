pipeline {
    agent any
    environment {
        APP_ENV = 'test'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'echo Building'
            }
        }
        stage('Test') {
            steps {
                sh 'echo Running tests'
            }
        }
        stage('Deploy') {
            when {
                branch 'master'
            }
            steps {
                withCredentials([string(credentialsId: 'deploy-token', variable: 'TOKEN')]) {
                    sh 'echo Deploying with a token'
                }
            }
        }
    }
    post {
        success {
            echo 'All stages passed'
        }
        failure {
            echo 'Something failed'
        }
    }
}
