pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/venkataAkshayareddy/maven-project.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean install'
            }
        }

        // Optional: SonarQube
        stage('SonarQube Analysis') {
            when {
                expression { return env.SONARQUBE != null }
            }
            steps {
                withSonarQubeEnv('My SonarQube Server') {
                    bat 'mvn sonar:sonar'
                }
            }
        }
    }
}
