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
        stage('start container') {
            steps {
                sh '/usr/local/bin/docker-compose --version'
                sh '/usr/local/bin/docker-compose up -d'                
                //sh 'docker-compose ps'
            }
        }
        stage('Run tests against the container') {
            steps {
                sh 'curl http://localhost:8888/param?query=demo | jq'
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
