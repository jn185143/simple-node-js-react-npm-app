pipeline {
    agent any

    stages {
        stage('Verify Branch') { 
            steps {
                echo "$GIT_BRANCH"
            }
        }
        stage('Build App'){
            steps{
                sh('npm install')
                sh('npm run build')
            }
            post{
                success{
                    echo 'App built successfully'
                }
                failure{
                    echo 'App failed to build'
                }
            }
        }
        stage('Run Test'){
            steps{
                sh('npm run test')
            }
            post{
                success{
                    echo 'App npm tests ran successfully'
                }
                failure{
                    echo 'App npm tests failed'
                }
            }
        }
        stage('Docker Build'){
            steps {
                sh('docker images -a')
                sh('''
                    docker images -a
                    docker build -t jenkins-pipeline-simple-app .
                    docker images -a
                    cd ..
                ''')
            }
        }
    }
}
