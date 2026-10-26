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
                bat '"C:\\Users\\Jahnavi\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pip install -r requirements.txt'
            }
        }
        stage('Test') {
            steps {
                bat '"C:\\Users\\Jahnavi\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pytest'
            }
        }
        stage('Compile') {
            steps {
                bat '"C:\\Users\\Jahnavi\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m compileall .'
            }
        }
        stage('Package') {
            steps {
                bat '"C:\\Users\\Jahnavi\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m zipfile -c app-package.zip app.py test_app.py'
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