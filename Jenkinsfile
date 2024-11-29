pipeline {
    agent any
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                bat 'npm install' // Use bat for Windows
            }
        }
        stage('Test') {
            steps {
                bat '"C:\\Program Files\\Git\\bin\\bash.exe" -c chmod +x ./jenkins/scripts/test.sh && ./jenkins/scripts/test.sh"' // Use Git Bash to run the script
            }
        }
    }
}
