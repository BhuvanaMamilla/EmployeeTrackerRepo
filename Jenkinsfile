pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/BhuvanaMamilla/EmployeeTrackerRepo.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
    post {
        success {
            echo 'Build and test succeeded!'
        }
        failure {
            echo 'Build or test failed.'
        }
    }
}
