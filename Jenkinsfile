pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the specific branch, e.g., 'master'
                git branch: 'main', url: 'https://github.com/BhuvanaMamilla/EmployeeTrackerRepo.git'
            }
        }
        stage('Build') {
            steps {
                cleanWs()
                sh './mvnw clean install || mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh './mvnw test || mvn test'
            }
        }
        stage('Publish Test Results') {
            steps {
                junit '**/target/surefire-reports/*.xml'
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
