pipeline{
    environment{
        registry= "hub.docker.com"
        registryCredential = 'docker'
        dockerImage = ''
        imagename= "app"
    }
    agent any
    stages{
        stage('git checkout'){
            steps{
                git([url: 'https://github.com/surendraasr4/techworld-js-docker-demo-app.git', branch: 'master', credentialsId: 'githubcreds3'])
            }
        }
        stage ('Docker build'){
            steps{
                script{
                    dockerImage = docker.build imagename
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
                    sh 'docker login -u surendradockerhubreg -p Sunrise.123'
                    sh 'docker tag app:latest surendradockerhubreg/hashedin:1.1'
                    sh 'docker push surendradockerhubreg/hashedin:1.1'
                    }
                }
            }
        }
                                                                  
    }


