pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Checkout code from GitHub
                git 'https://github.com/username/repository-name.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install dependencies, upgrade pip if necessary
                sh 'python -m pip install --upgrade pip'
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                // Run tests using unittest
                sh 'python -m unittest discover'
            }
        }
    }


    post {
        always {
            // Archive the test reports
            junit '**/test-reports/*.xml'
        }
        success {
            echo 'Tests passed successfully!'
        }
        failure {
            echo 'Tests failed!'
        }
    }
}
