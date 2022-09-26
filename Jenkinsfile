pipeline{
    environment{
        registry= "surendradockerhubreg/hashedin"
        registryCredential = 'docker'
        dockerImage = ''
    }
    agent any
    stages{
        stage('git checkoutn'){
            steps{
                git credentials Id: 'cred',
                url: 'https://github.com/surendraasr4/techworld-js-docker-demo-app.git'
            }
        }
        stage ('Docker build'){
            steps{
                script{
                    dockerImage = docker.build registry + ":$GIT_COMMIT"
                }
            }
        }
        stage ('Approval to push docker image'){
            input{
                message "Do you want to push docker image to docker hub?"
            }
                steps {
                    sh 'echo "Pushing docker image"'

                    }
            }
        stage('Docker image push'){
            steps{
                script{
                    docker.withRegistry( '',registryCredential ) {
dockerImage.push()
                    }
                }
            }
        }
                                                                  
    }
}
