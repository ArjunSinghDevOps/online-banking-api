pipeline {
    agent any

    tools {
        jdk 'JDK'
        maven 'Maven'
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/ArjunSinghDevOps/online-banking-api.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh '''
                        mvn sonar:sonar \
                        -Dsonar.projectKey=online-banking-api \
                        -Dsonar.projectName=online-banking-api
                    '''
                }
            }
        }
    }
}