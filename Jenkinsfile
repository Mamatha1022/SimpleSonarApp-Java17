pipeline {
    agent any

    environment {
        SONARQUBE_TOKEN = credentials('sonar-token')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/Mamatha1022/SimpleSonarApp-Java17.git',
                        credentialsId: 'github-token'
                    ]]
                ])
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                echo 'Running SonarQube scan...'
            }
        }

        stage('Quality Gate') {
            steps {
                echo 'Checking SonarQube quality gate...'
            }
        }
    }
}
