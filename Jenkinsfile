pipeline {
    agent none

    stages {
        stage('Checkout') {
            agent { label 'windows' }
            steps {
                echo 'Cloning the repo...'
                git 'https://github.com/RushaDutta/DevOpsAssignment.git'
            }
        }

        stage('Install Dependencies') {
            agent { label 'windows' }
            steps {
                echo 'Installing packages...'
                bat 'npm install'
            }
        }

        stage('Test') {
            agent { label 'windows' }
            steps {
                echo 'Running tests...'
                bat 'npm test'
            }
        }

        stage('Build') {
            agent { label 'windows' }
            steps {
                echo 'Building the app...'
                bat 'npm run build'
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            agent { label 'windows' }
            steps {
                echo 'Deploying app...'
                bat 'deploy.bat'
            }
        }
    }

    post {
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
