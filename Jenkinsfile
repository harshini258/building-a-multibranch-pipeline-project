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
                bat '"C:\\Program Files\\Git\\bin\bash.exe" -c "./jenkins/scripts/test.sh"'
            }
        }
    }
}

