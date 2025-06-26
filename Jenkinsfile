pipeline {
    agent any

    stages {


        stage('Run only on main or feature branches'){
            when{
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps {
                echo 'This will run only on main or feature/* branches'
            }
        }

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