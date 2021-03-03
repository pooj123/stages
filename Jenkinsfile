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
        stage ('Static Analysis') {
            steps {
                sh ' ./node_modules/eslint/bin/eslint.js -f checkstyle src > eslint.xml'
            }
            post {
                always {
                    recordIssues enabledForFailure: true, aggregatingResults: true, tool: checkStyle(pattern: 'eslint.xml')
                }
            }
        }
    }

    }
}