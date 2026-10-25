
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install') {
            steps {
                bat 'python -m pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                bat 'python -m pytest'
            }
        }

        stage('Compile') {
            steps {
                bat 'python -m compileall .'
            }
        }

        stage('Package') {
            steps {
                bat 'python -m zipfile -c app-package.zip app.py test_app.py'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'app-package.zip',
                             allowEmptyArchive: true
        }
    }
}
