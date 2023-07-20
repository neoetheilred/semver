pipeline {
    agent any

    stages {
        stage('init') {
            steps {
                script {
                    String[] tags = sh(script: "git tags | tr - \~ | sort -V | tr \~ -")
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