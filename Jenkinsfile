pipeline {
    agent { docker { image 'python:3.12.1-alpine3.19' } }
    options {
    // Keep the 10 most recent builds
    buildDiscarder(logRotator(numToKeepStr:'3')) 
  }
    stages {
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
        stage('disk size') {
            steps {
                sh 'df -h'
            }
        post {
            success {
                echo "disk sizes check"
            }
        }

        }        
    }
    post {
        always {
            echo "Send notifications for result: ${currentBuild.result}"
        }
    }
}


