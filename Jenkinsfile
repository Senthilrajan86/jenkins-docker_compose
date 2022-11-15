pipeline {
    agent any
    stages {
        stage("verfiy tooling"){
            steps {
                sh '''               
                    curl --version
                    jq --version
                '''
            }
        }    
        stage('start container') {
            steps {
                sh 'docker compose up'
                sh 'docker compose ps'
            }
        }
        stage('Run tests against the container') {
            steps {
                sh 'curl http://localhost:3000/param?query=demo | jq'
            }
        }
    }
    post {
        always {
            sh 'docker compose down'
            sh 'docker compose ps'
        }
    }
}