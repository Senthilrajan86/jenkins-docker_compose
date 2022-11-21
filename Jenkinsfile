pipeline {
    agent any
    stages {
        stage("verify tooling"){
            steps {
                sh '''               
                    curl --version                    
                '''
            }
        }
        stage('Verification of the container') {
            steps {
                sh '/usr/local/bin/docker-compose ps'
                if pgrep -x "docker-compose" >/dev/null
                then                
                sh '/usr/local/bin/docker-compose down'                
                fi
                //sh 'docker-compose ps'
            }
        }
        stage('start container') {
            steps {
                sh '/usr/local/bin/docker-compose --version'
                sh '/usr/local/bin/docker-compose up -d'                
                //sh 'docker-compose ps'
            }
        }
        stage('Run tests against the container') {
            steps {
                sh 'docker-compose ps'
                //sh 'curl http://localhost:3000/param?query=demo | jq'
            }
        }
    }
    //post {
    //    always {
      //      sh 'docker-compose down'
        //    sh 'docker-compose ps'
        //}
    //}
}
