pipeline {
    agent any
    tools {
        maven 'Maven' // Use the name you provided in the Global Tool Configuration
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/jonnekoi/TimeCalculator.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'  // Execute the Maven build in a shell
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'  // Run the Maven tests in a shell
            }
        }

        stage('Code Coverage') {
            steps {
                jacoco execPattern: '**/target/jacoco.exec'  // Jacoco code coverage step
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'  // Publish JUnit test reports
            jacoco execPattern: '**/target/jacoco.exec'  // Publish Jacoco code coverage reports
        }
    }
}
