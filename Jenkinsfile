pipeline {
    agent {
        docker {
            image 'node:18-alpine'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    environment {
        USER = 'jenkins'  // You can set user in the environment
    }
    stages {
        stage('rk docker build') {
            steps {
                sh "echo 'Hello World'"
                sh 'npm --version'
            }
        }
        stage('rk test') {
            steps {
                sh "echo 'test is fine, too'"
            }
        }
    }
}
