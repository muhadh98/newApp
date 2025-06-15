// Jenkinsfile
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code from GitHub...'
                git url: 'https://github.com/your-username/your-repo.git', branch: 'main'
            }
        }
        stage('Compile') {
            steps {
                echo 'Compiling the project...'
                sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
                echo 'Test results:'
                sh 'cat target/surefire-reports/*.txt || echo "No test report found."'
            }
        }
        stage('Install') {
            steps {
                echo 'Installing the package...'
                sh 'mvn install'
            }
        }
        stage('Build') {
            steps {
                echo 'Packaging the application...'
                sh 'mvn package'
                echo 'Artifacts generated:'
                sh 'ls -lh target'
            }
        }
    }
    post {
        always {
            echo 'Pipeline finished. Collecting test reports...'
            junit '**/target/surefire-reports/*.xml'
        }
        success {
            echo 'Build completed successfully! Check above for details.'
        }
        failure {
            echo 'Build failed. Please review the logs above for errors.'
        }
    }
}