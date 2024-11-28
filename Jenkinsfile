pipeline {
    agent any
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                bat '"C:\\Program Files\\Git\\bin\\git.exe" -c "./jenkins/scripts/test.sh"'
            }
        }
    }
}

