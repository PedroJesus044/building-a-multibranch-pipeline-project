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

    stages {
        stage('SSH-test') {
            // steps {
            //     sshagent (credentials: ['rocky-8']) {
            //         sh 'ssh -o StrictHostKeyChecking=no -l cloudbees 192.168.32.1 uname -a'
            //     }
            // }
            steps {

                withCredentials([sshUserPrivateKey(credentialsId: 'rocky-8-key', keyFileVariable: 'MY_SSH_KEY')]) {

                    sh '''

                    ssh -i $MY_SSH_KEY root@192.168.32.1 "ls -la"

                    '''

                }

            }

        }
        stage('Build') {
            steps {
                // sh '/bin/docker pull node:lts'
                sh 'echo "build"'
            }
        }
        stage('Test') {
            steps {
                // sh './jenkins/scripts/test.sh'
                sh 'echo "test"'
            }
        }
    }
}

