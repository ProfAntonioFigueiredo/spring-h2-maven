pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // 'dir' pode ser deixado vazio se você já está no diretório correto
                dir('.') { 
                    sh 'mvn clean package'
                }
            }
        }

        stage('Deploy') {
            steps {
                // Se o docker-compose.yml estiver no mesmo diretório, use '.'
                dir('.') {
                    sh "cd /home/pf1776/spring-h2-maven"
                    sh 'sudo -S docker compose up -d'
                }
            }
        }
    }
}
