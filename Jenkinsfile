pipeline {
    agent any
    tools {
        maven 'Maven-3.9'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
    post {
        success {
            echo '✅ Pipeline réussi!'
        }
        failure {
            echo '❌ Pipeline échoué!'
        }
    }
}

