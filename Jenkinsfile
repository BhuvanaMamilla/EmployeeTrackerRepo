pipeline {
    agent any
    tools {
        maven 'Maven 3.8.6' // Make sure this matches the Maven installation name in Jenkins configuration
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/BhuvanaMamilla/EmployeeTrackerRepo.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    // Use Maven wrapper if available
                    if (fileExists('mvnw')) {
                        sh './mvnw clean install'
                    } else {
                        sh 'mvn clean install'
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Use Maven wrapper if available
                    if (fileExists('mvnw')) {
                        sh './mvnw test'
                    } else {
                        sh 'mvn test'
                    }
                }
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
