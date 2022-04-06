pipeline {
    agent any
    stages {
        stage('Clean') {
            steps {
                sh 'docker stop helloworld && docker rm helloworld || true'
            }
        }
      stage('Build') {
            steps {
                sh 'docker build --tag helloworld:$BUILD_NUMBER .'
            }
        }
        stage('Test') {
            steps {
                sh 'docker run --name helloworld -p 1337:1337 helloworld:$BUILD_NUMBER node /var/www/index.js &'
            }
        }
        
    }
}
