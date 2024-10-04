pipeline {
    agent any
    environment {
        CI = 'true'
    }

    // def remote = [:]
    // remote.name = 'test'
    // remote.host = '192.168.32.1'
    // remote.user = 'root'
    // remote.password = 'a478s236d159f'
    // remote.allowAnyHosts = true

    node {
        sshagent (credentials: ['deploy-dev']) {
            sh 'ssh -o StrictHostKeyChecking=no -l cloudbees 192.168.32.1 uname -a'
        }
    }

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
    }
}

