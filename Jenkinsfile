pipeline {
    agent {
        docker {
            image 'node:18-alpine'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
            reuseNode true
        }
    }
    // environment {
    //     USER = 'jenkins'  // You can set user in the environment
    // }
    stages {
        stage('rk build') {
            steps {
                sh '''
                    echo 'step 1'
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
        stage('rk test') {
            steps {
                sh ''' 
                    test -f build/index.html
                    npm test 
                '''
            }
        }
    }
    post {
        always {
            junit 'test-results/junit.xml'
        }
    }
}
