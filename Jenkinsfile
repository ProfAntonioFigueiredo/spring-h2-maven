pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                dir('pom.xml') {
                    sh 'mvn clean package'
                }
            }
        }

        stage('Deploy') {
            steps {
                dir('jenkins') {
                    sh 'docker-compose up -d'
                }
            }
        }
    }
}
