pipeline {
    agent any

    stages {
        stage('Checkout the repository') {
            steps {
                checkout scm
            }
        }

        stage('Restore the project') {
            steps {
                script {
        if (isUnix()) {
            sh 'dotnet restore'
        } else {
            bat 'dotnet restore'
        }
    }
            }
        }


        stage('Build the project') {
            steps {
                script {
                if (isUnix()) {
                    sh 'dotnet build'
                } else {
                    bat 'dotnet build'
                }
                    }
            }
        }

        stage('Test') {
            steps {
                script {
                if (isUnix()) {
                    sh 'dotnet test'
                } else {
                    bat 'dotnet test'
                }
                    }
            }
        }

    }
}