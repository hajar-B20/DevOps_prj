pipeline {
    agent any
    
    tools {
        // Utilisez le nom EXACT que vous avez configuré dans Jenkins
        maven 'Maven3'
        jdk 'JDK17'
    }
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/hajar-B20/DevOps_prj.git'
            }
        }
        
        stage('Build') {
            steps {
                echo '🔨 Compilation du projet Java avec Maven...'
                sh 'mvn clean compile'
            }
        }
        
        stage('Test') {
            steps {
                echo '🧪 Exécution des tests unitaires...'
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
    
    post {
        success {
            echo '✅ Pipeline terminé avec succès ! Build et tests OK.'
        }
        failure {
            echo '❌ Pipeline échoué. Vérifiez les logs ci-dessus.'
        }
    }
}
