pipeline {
    agent any

    stages {
        stage('init') {
            steps {
                sh "echo hello"
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}