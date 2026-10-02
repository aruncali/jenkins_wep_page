pipeline{
    agent any

    stages{
        stage('build image'){
            steps{
                sh 'docker build -t page1:latest .'
            }
        }
        stage('deploy image'){
            steps{
                sh 'docker rm -f page1 || true'
                sh 'docker run -d -p 8000:80 --name webpage page1:latest'
                sh 'docker images'
                sh 'docker ps'
                }
        }
     post{
       success { echo ' deployed open in http://localhost:8000' }
       failed { echo ' something is failed, chech the logs ' }
    }
}
}
