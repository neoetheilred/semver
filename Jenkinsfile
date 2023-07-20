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

Tuple3 VersionStrToTuple3(String version) {
    return new Tuple3(version.split('.').collect {it.toInteger()})
}

Tuple3 NextMajorVersion(Tuple3 version) {
    return new Tuple3(version.v1+1, 0, 0)
}