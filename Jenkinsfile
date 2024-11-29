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
                script {
                    // Check if the script exists and is executable
                    if (fileExists('./jenkins/scripts/test.sh')) {
                        bat '"C:\\Program Files\\Git\\bin\\bash.exe" -c ./jenkins/scripts/test.sh' // Directly run the script with Git Bash
                    } else {
                        error "test.sh script not found!"
                    }
                }
            }
        }
    }
}
