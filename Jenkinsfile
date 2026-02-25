pipeline {
    agent any

    tools {
        maven 'Maven 3'
        jdk 'Java 17'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/safwen-elmastouri/student-management.git'
            }
        }

        stage('Maven build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
        stage('SONARQUBE') {
        environment {
            SONAR_HOST_URL = 'http://192.168.33.10:9000/'
            SONAR_AUTH_TOKEN = credentials('sonarqube')
        }
            steps {
                sh 'mvn sonar:sonar -Dsonar.projectKey=devops_git -Dsonar.host.url=$SONAR_HOST_URL -Dsonar.token=$SONAR_AUTH_TOKEN'
            }
        }
    }
}
