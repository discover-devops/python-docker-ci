pipeline {

    agent { label 'my_slave' }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/discover-devops/python-docker-ci.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t python-ci-lab .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f python-container || true
                docker run -d -p 5000:5000 --name python-container python-ci-lab
                '''
            }
        }

    }
}