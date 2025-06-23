pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                    }
            }
            steps {
                sh '''
                    ls -altr
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -altr
                '''
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                    }
            }
            steps  {
                echo 'Test Stage'
                sh '''
                test -f build/index.html
                npm test
                ''' 
            }
            
        }
    }
}
