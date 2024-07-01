pipeline {
    agent any
    tools {
        maven 'Maven 3.8.1'  // Ensure the name matches what you configured in Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Blaundos/sample-project.git'
            }
        }
        stage('Compile') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Code Review') {
            steps {
                sh 'mvn checkstyle:check'
            }
        }
        stage('Unit Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
        // Add any additional stages like deployment here
    }
}
