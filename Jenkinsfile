pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/codesbyUmair/Lab11.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp:latest .'
            }
        }

        stage('Run Docker Image') {
            steps {
                sh 'docker run -d -p 80:80 myapp:latest'
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-hub-credentials') {
                        docker.image('myapp:latest').push()
                    }
                }
            }
        }

        

        
    }
}
