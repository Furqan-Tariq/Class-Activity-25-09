pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Clone only the main branch
                git branch: 'main', url: 'https://github.com/Furqan-Tariq/Class-Activity-25-09.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Assuming you have a requirements.txt file for Python dependencies
                bat 'pip install -r requirements.txt'
            }
        }



        stage('Run Tests') {
            steps {
                // Run linting and formatting first, then run tests
                bat '''
                echo Running flake8 linter...
                flake8 .  --ignore=E501

                echo Running black for formatting...
                black --check .

                echo Running Python unit tests...
                pytest testfile.py --disable-warnings
                '''
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
            echo 'Come on'
        }
    }
}
