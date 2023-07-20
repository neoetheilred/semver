pipeline {
    agent any

    stages {
        stage('init') {
            sh "echo hello"
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}