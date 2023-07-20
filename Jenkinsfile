import groovy.lang.Tuple

pipeline {
    agent any

    stages {
        stage('init') {
            steps {
                script {
                    sh "git fetch --tags"
                    String[] tags = sh(script: '''git tag | tr '-' '~'| sort -r -V | tr '~' '-' ''', returnStdout: true).split()
                    String latest = tags[0] // Assuming that all versions are of format X.Y.Z, with no additions
                    sh "echo ${latest}"
                    sh "echo ${VersionToTuple3(latest)}"
                    sh "echo ${NextMajorVersion(VersionStrToTuple3(latest))}"
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

Tuple VersionStrToTuple3(String version) {
    return new Tuple(version.split('.').collect {it.toInteger()})
}

Tuple NextMajorVersion(Tuple version) {
    return new Tuple(version.v1+1, 0, 0)
}