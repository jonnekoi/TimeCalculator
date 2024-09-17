
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/jonnekoi/TimeCalculator.git'
            }
        }

        stage('Build') {
            steps {
                 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                 'mvn test'
            }
        }

        stage('Code Coverage') {
            steps {
                jacoco execPattern: '**/target/jacoco.exec'
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
            jacoco execPattern: '**/target/jacoco.exec'
        }
    }
}

