pipeline {
    agent {
        docker {
            image 'node:15.10.0-alpine3.10'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true' 
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }  
        }
        stage ('Linting') {
            steps {
                sh 'npm run lint'
            }
        }
    }
}