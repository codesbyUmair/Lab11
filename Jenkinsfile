pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                sh 'echo Checkout passed'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        

        stage('Build Docker Image') {
            steps {
                sh 'echo docker_build_-t_myapp:latest_.'
            }
        }

        stage('Run Docker Image') {
            steps {
                sh 'echo docker_run_-d_-p_80:80_myapp:latest'
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    echo 'Pushing Docker image to Docker Hub...'
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-hub-credentials') {
                        docker.image('myapp:latest').push()
                    }
                    echo 'Docker image pushed successfully.'
                }
            }
        }

        
        
    }
}
