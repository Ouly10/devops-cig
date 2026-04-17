pipeline {
    agent any

    stages {

        stage('Cloner le repo') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/TIO-Moussa/devops-cig.git'
            }
        }

        stage('Build & Démarrer avec Docker Compose') {
            steps {
                sh 'docker compose down || true'
                sh 'docker compose up -d --build'
            }
        }

        stage('Vérifier les conteneurs') {
            steps {
                sh 'docker ps'
            }
        }
    }

    post {
        success {
            echo '✅ Déploiement réussi ! App disponible sur http://localhost:8080'
        }
        failure {
            echo '❌ Le pipeline a échoué.'
        }
    }
}
