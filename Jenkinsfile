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
                    sshpass -p '${env.USERNAME_PSW}' ssh -o StrictHostKeyChecking=no ${env.USERNAME_USR}@remote-server-ip '
                    cd /caminho/para/o/docker-compose &&
                    docker-compose up -d
                    '
                    """
                }
            }
        }
    }
}
