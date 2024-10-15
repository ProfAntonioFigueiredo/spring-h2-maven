pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy') {
            environment {
                USERNAME = credentials('ssh-user-password')
            }
            steps {
                script {
                    // Executa comandos na máquina remota usando usuário e senha
                    sh """
                    sshpass -p '${env.USERNAME_PSW}' ssh -o StrictHostKeyChecking=no ${env.USERNAME_USR}@http://52.152.228.195'
                    cd /home/pf1776/spring-h2-maven &&
                    docker-compose up -d
                    '
                    """
                }
            }
        }
    }
}
