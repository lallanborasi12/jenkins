pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo "Code downloaded successfully"
            }
        }

        stage('Workspace') {
            steps {
                sh 'pwd'
                sh 'ls -la'
            }
        }

        stage('Git Information') {
            steps {
                sh 'git branch'
                sh 'git log --oneline -5'
            }
        }

        stage('Finish') {
            steps {
                echo "Pipeline completed successfully"
            }
        }
    }
}
