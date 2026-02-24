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

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

    }
}
