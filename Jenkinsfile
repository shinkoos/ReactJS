pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/shinkoos/ReactJS.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }
        stage('Build') {
            steps {
                bat 'npm run build'
            }
        }
        stage('Test') {
            steps {
                bat 'npm run test'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                bat 'npm run sonar'
            }
        }
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t react-jenkins-pipeline .'
            }
        }
                stage('Deploy') {
            steps {
                bat 'npm run start'
            }
        }
    }
    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build and deployment failed!'
        }
    }
}