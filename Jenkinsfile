pipeline {
    agent {
        docker {
            image 'python3.9'
        }
    }
    stages {
        stage ('Checkout') {
            steps {
                checkout scmGit(
                    branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/Doseman01/fastapi-book-project.git']])
            }
        }
        stage('Install dependencies') {
            steps {
                sh 'pip install -r requirements'      
            }
        }
        stage ('Test') {
            steps {
                sh 'pytest'
            }
        }
    }
}
