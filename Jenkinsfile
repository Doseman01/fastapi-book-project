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
                sh 'pipx install -r requirements.txt'
            }
        }
        stage ('Test') {
            steps {
                sh 'pytest'
            }
        }
    }
}
