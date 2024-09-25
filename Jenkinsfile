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
                bat '''
                python --version
                pip --version
                pip install -r requirements.txt
                '''
            }
        }




        stage('Run Tests') {
            steps {
                bat '''
                pytest testfile.py --disable-warnings --junitxml=reports/results.xml
                '''
            }
            post {
                always {
                    junit 'reports/results.xml' // Ensure the test report is generated
                }
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
