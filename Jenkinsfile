pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                dir('.') {
                    sh 'mvn clean package'
                }
            }
        }

        stage('Deploy') {
            steps {
                dir('.') {
                    sh 'docker-compose up -d'
                }
            }
        }
    }
}
