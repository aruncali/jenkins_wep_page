pipeline {
    agent any

    stages {

        stage('Build Image') {
            steps {
                sh 'docker build -t page1:latest .'
            }
        }

        stage('Deploy Image') {
            steps {
                sh 'docker rm -f webpage || true'
                sh 'docker run -d -p 8000:80 --name webpage page1:latest'
                sh 'docker images'
                sh 'docker ps'
            }
        }
    }

    post {
        success {
            echo 'Deployment successful. Open http://ip:8080'
        }

        failure {
            echo 'Something failed. Check the Jenkins console logs.'
        }
    }
}
