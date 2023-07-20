pipeline {
    agent any

    stages {
        stage('init') {
            steps {
                script {
                    sh "git fetch --tags"
                    String[] tags = sh(script: "git tag", returnStdout: true).split()
                    sh "echo ${tags.join(',')}"
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}