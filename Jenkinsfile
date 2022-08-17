pipeline {
    agent any

    stages {
        stage('Verify Branch') { 
            steps {
                echo "$GIT_BRANCH"
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
        stage('Prepare Enviornment'){
            steps {
                sh('docker image prune')    
                sh('docker run -dp 3000:3000 --name test-app jenkins-pipeline-simple-app')
            }
        }
        stage('Run Test'){
            steps{
                sh('docker exec test-app npm test')
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
    }
}
