pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/muhadh98/newApp.git', branch: 'main'
            }
        }
        stage('install') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn package'
            }
        }

        stage('compile') {
            steps {
                sh 'mvn compile'
            }
        }
    }
}