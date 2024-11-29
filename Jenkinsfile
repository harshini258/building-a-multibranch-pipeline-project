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
        stage('Deliver for development') {
            when {
                branch 'development' 
            }
            steps {
                bat '"C:\\Program Files\\Git\\bin\\bash.exe" -c ./jenkins/scripts/deliver-for-development.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)', timeout:300
                bat '"C:\\Program Files\\Git\\bin\\bash.exe" -c ./jenkins/scripts/kill.sh'
            }
        }
        stage('Deploy for production') {
            when {
                branch 'production'  
            }
            steps {
                bat '"C:\\Program Files\\Git\\bin\\bash.exe" -c ./jenkins/scripts/deploy-for-production.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)', timeout:300
                bat '"C:\\Program Files\\Git\\bin\\bash.exe" -c ./jenkins/scripts/kill.sh'
            }
        }
    }
}

