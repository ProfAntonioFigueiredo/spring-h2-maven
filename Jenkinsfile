pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                dir('spring-h2-maven') {
                    sh 'mvn clean package'
                }
            }
        }

        stage('Deploy') {
            steps {
                dir('spring-h2-maven') {
                    sh 'docker-compose up -d'
                }
            }
        }
    }
}
