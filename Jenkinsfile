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
                sh './mvnw clean package -Dspring.kafka.bootstrap-servers=host.docker.internal:29092'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        always {
            sh 'docker-compose down'
        }
    }
}