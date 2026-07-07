pipeline {
    agent any

    environment {
        SERVER = "ubuntu@65.0.102.170"
        DEPLOY_PATH = "/var/www/html"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build React App') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Verify Build') {
            steps {
                sh 'ls -la build'
            }
        }

        stage('Deploy to EC2') {
            steps {
                sh '''
                rsync -avz --delete build/ $SERVER:$DEPLOY_PATH/
                '''
            }
        }

        stage('Deployment Verification') {
            steps {
                sh '''
                ssh $SERVER "ls -la /var/www/html"
                '''
            }
        }
    }
}
