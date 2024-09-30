pipeline{
    agent any

    //Section to define global variables
    environment{
        INDEX = 'index.html'
    }
    stages{
        //Section to build the application
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
        //Section to perform Test
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
                    #ls -la
                    test -f build/$INDEX && echo "file exist" || echo "file not extist"
                    npm test
                '''
            }
        }
    }

    //These section is used for extract the Junit information
    post{
        always{
            junit 'test-results/junit.xml'
        }
    }
    
}