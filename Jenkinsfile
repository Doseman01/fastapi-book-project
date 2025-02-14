pipeline {
    agent any 
    stages {
        stage ('Checkout') {
            steps {
                checkout scmGit(
                    branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/Doseman01/fastapi-book-project.git']])
            }
        }
        stage('Install dependencies') {
            steps {
                sh '''
                apt-get install -y python3.9 python-pip 
                python3 -m venv venv
                source venv/bin/activate
                pip install --upgrade pip
                pip install -r requirements
                '''          
            }
        }
        stage ('Test') {
            steps {
                sh '''
                source venv/bin/activate
                pytest
                '''
            }
        }
    }
}
