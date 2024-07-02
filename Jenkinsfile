pipeline {
    agent any

    tools {
        maven 'Maven 3.9.7'  
    }
    environment {
        PATH = "/usr/local/sdkman/candidates/maven/current/bin:${env.PATH}"
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
                // Add an echo here to find the WAR file
                sh 'ls -l target/*.war' 
            }
        }

        stage('Deploy to Local Tomcat') {
            steps {
                sh '''
                WAR_FILE=$(ls target/*.war)
                echo "Deploying WAR file: $WAR_FILE" 
                cp $WAR_FILE ~/tomcat/webapps/
                '''
            }
        }
    }
}
