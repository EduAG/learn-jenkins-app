pipeline{
    agent any

    environment{
        INDEX = 'index.html'
    }
    stages{
        stage('Build'){
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps{
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
        stage('Test'){
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps{
                echo 'Test stages'
                sh '''
                    ls -la
                    test -f build/$INDEX && echo "file exist" || echo "file not extist"
                    npm test
                '''
            }
        }
    }
    
}