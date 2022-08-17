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
                    cd simple-node-js-react-npm-app
                    docker images -a
                    docker build -t jenkins-pipeline-simple-app .
                    docker images -a
                    cd ..
                ''')
            }
        }
    }
}
