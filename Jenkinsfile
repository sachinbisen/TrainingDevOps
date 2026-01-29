pipeline {
    agent any

    environment {
        PATH = "/opt/homebrew/bin:/usr/bin:/bin:/usr/sbin:/sbin"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'dotnet --version'
                sh 'dotnet restore'
                sh 'dotnet build --configuration Release'
            }
        }

        stage('Test') {
            steps {
                sh 'dotnet test --no-restore --configuration Release'
            }
        }

        stage('Publish') {
            steps {
                sh 'dotnet publish --no-restore --configuration Release -o publish'
            }
        }
    }

    post {
        success {
            echo 'Build, test, and publish successful!'
        }
    }
}
