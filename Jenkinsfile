pipeline {
    agent any
    environment {
        CI = 'true'
    }

    def remote = [:]
    remote.name = 'test'
    remote.host = '192.168.32.1'
    remote.user = 'root'
    remote.password = 'a478s236d159f'
    remote.allowAnyHosts = true

    stages {
        stage('Build') {
            steps {
                sh '/bin/docker pull node:lts'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }

        stage('Remote SSH') {
        sshRemove remote: remote, path: "abc.sh"
        }
    }
}

