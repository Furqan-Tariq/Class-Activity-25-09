pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Furqan-Tariq/Class-Activity-25-09.git'
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
                // Run tests and generate JUnit XML report
                sh 'python -m unittest discover -s tests -p "*.py" > test-reports/results.xml'
            }
        }
    }

    post {
        always {
            // Archive the test reports
            junit 'test-reports/*.xml'
        }
        success {
            echo 'Tests passed successfully!'
        }
        failure {
            echo 'Tests failed!'
        }
    }
}
