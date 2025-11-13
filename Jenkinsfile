pipeline {
    agent any

    environment {
        GIT_REPO = "https://github.com/muneebaslam157/ezyshopper.git"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: "${GIT_REPO}"
            }
        }

        stage('Build Containers') {
            steps {
                sh 'docker-compose -f docker-compose-jenkins.yml down || true'
                sh 'docker-compose -f docker-compose-jenkins.yml build'
            }
        }

        stage('Run Containers') {
            steps {
                sh 'docker-compose -f docker-compose-jenkins.yml up -d'
            }
        }

        stage('Verify Containers') {
            steps {
                sh 'docker ps'
            }
        }
    }
}
