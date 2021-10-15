pipeline {
    // master executor should be set to 0
    agent any
    stages {
        stage('Pull Latest Image') {
            steps {
                //sh
                bat "docker pull pengzsdocker/selenium-docker"
            }
        }
        stage('Start Grid') {
            steps {
                //sh
                bat "docker-compose up -d hub chrome firefox"
            }
        }
        stage('Run Test') {
            steps {
                //sh
                bat "docker-compose up search-chrome search-firefox login-chrome login-firefox"
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'output/**'
            bat "docker-compose down"
        }
    }
}