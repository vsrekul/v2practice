pipeline{
    agent any
    stages{
        stage("checkout"){
            steps{
                checkout scmGit(branches: [[name: 'main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/vsrekul/v2practice.git']])
            }
        }
        stage("docker build"){
            //docker run -d -p80:80 --name alpin-old vsrekul/apachev2
            agent { label 'docker' } 
            steps{
                script{
                    sh '''
                      docker build -t vsrekul/apachev2 .
                      docker push vsrekul/apachev2
                      
                    '''
                }
            }
        }
    }
}