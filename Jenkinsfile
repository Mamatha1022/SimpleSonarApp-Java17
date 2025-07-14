pipeline {
    agent any

    environment {
        SONARQUBE_TOKEN = credentials('sonar-token')
    }

    stages {
        stage('Clone') {
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
    }

        stage('Build') {
            steps {
                echo 'Building project...'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                echo "Running SonarQube Analysis with token: ${env.SONARQUBE_TOKEN}"
            }
        }

        stage('Quality Gate') {
            steps {
                timeout(time: 5, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }

