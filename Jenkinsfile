pipeline {
    agent any
    tools {
        maven 'Maven_3.9.7' 
    }
    environment {
        PATH = "${tool 'Maven_3.9.7'}/bin:${env.PATH}"
    }
    stages {
        stage('Checkout') {
            steps {
                echo "Checking out code from repository..."
                git 'https://github.com/Blaundos/sample-project.git'
            }
        }
        stage('Compile') {
            steps {
                echo "Compiling the source code..."
                sh 'mvn compile'
            }
        }
        stage('Code Review') {
            steps {
                echo "Running code style analysis..."
                sh 'mvn checkstyle:check'
            }
        }
        stage('Unit Test') {
            steps {
                echo "Running unit tests..."
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                echo "Packaging the application (WAR)..."
                sh 'mvn package'
            }
        }
        stage('Deploy to Local Tomcat') {
            steps {
                echo "Copying WAR file to Tomcat webapps directory..."
                sh '''
                cp target/my-web-app.war ~/tomcat/webapps/
                '''
                echo "Deployment to Tomcat complete!"
            }
        }
    }
}
