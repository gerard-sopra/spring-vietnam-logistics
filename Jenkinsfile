pipeline {
    agent any

    stages {
        stage('Start Infrastructure') {
            steps {
                sh 'docker-compose up -d'
            }
        }

        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
        }
    }

    post {
        always {
            sh 'docker-compose down'
        }
    }
}