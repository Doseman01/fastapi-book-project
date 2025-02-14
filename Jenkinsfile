
pipeline {
    agent {
        docker {
            image 'python:3.9'
        }
    }
    stages {
        stage ('Checkout') {
            steps {
                checkout scmGit(
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://github.com/Doseman01/fastapi-book-project.git']]
                )
            }
        }
        stage('Install dependencies') {
            steps {
                sh '''
                python3 -m venv venv
                venv/bin/pip install --upgrade pip
                venv/bin/pip install -r requirements.txt
                '''
            }
        }
        stage ('Test') {
            steps {
                sh '''
                venv/bin/python -m pytest --maxfail=1 
                '''
            }
        }
    }
}
