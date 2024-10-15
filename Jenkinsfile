pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'ssh-user-password', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh """
                    sshpass -p "${PASSWORD}" ssh -o StrictHostKeyChecking=no ${USERNAME}@52.152.228.195 '
                    cd /home/pf1776/spring-h2-maven &&
                    docker-compose up -d
                    '
                    """
                }
            }
        }
    }
}

