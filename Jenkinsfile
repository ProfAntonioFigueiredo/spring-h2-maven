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
                    sh pwd
                    sh 'docker-compose up -d'
                }
            }
        }
    }
}
