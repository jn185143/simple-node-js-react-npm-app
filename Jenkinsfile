pipeline {
    agent any

    environment {
        // username="user"
        // password="password"
        uri="https://github.com/jn185143/simple-node-js-react-npm-app.git"
    }

    stages {
        stage('Verify Branch') { 
            steps {
                echo "$GIT_BRANCH"
            }
        }
        stage('Test') { 
            
            steps {
                credentials_Id=GitTaggingUtils.getGitCredentials([repo_uri:"${vars.repo_uri}"])
                 withCredentials([usernamePassword(credentialsId: "$credentials_Id", passwordVariable: 'password', usernameVariable: 'userName')]) {
                    withEnv(["repo_uri=$uri"]){
                        sh('echo test ' + '${repo_uri/github/"$userName:$password@github"}' + ' test2')
                    }
                }
            }
        }
        // stage('Docker Build'){
        //     steps {
        //         sh('docker images -a')
        //         sh('''
        //             docker images -a
        //             docker build -t jenkins-pipeline-simple-app .
        //             docker images -a
        //             cd ..
        //         ''')
        //     }
        // }
        // stage('Prepare Enviornment'){
        //     steps {
        //         sh('docker image prune')    
        //         sh('docker run -dp 3000:3000 --name test-app jenkins-pipeline-simple-app')
        //     }
        // }
        // stage('Run Test'){
        //     steps{
        //         sh('docker exec test-app npm test')
        //     }
        //     post{
        //         success{
        //             echo 'App npm tests ran successfully'
        //         }
        //         failure{
        //             echo 'App npm tests failed'
        //         }
        //     }
        // }
    }
}
