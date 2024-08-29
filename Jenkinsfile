pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests using Selenium...'
            }
            post {
                success {
                    emailext(
                        to: 'psahmadtc@gmail.com',
                        subject: 'Unit and Integration Tests Passed',
                        body: 'Unit and integration tests passed successfully.',
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: 'psahmadtc@gmail.com',
                        subject: 'Unit and Integration Tests Failed',
                        body: 'Unit and integration tests failed. Details in Logs.',
                        attachLog: true
                    )
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing the code using SonarQube...'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan using OWASP Dependency-Check...'
            }
            post {
                success {
                    emailext(
                        to: 'psahmadtc@gmail.com',
                        subject: 'Security Scan Passed',
                        body: 'Security scan passed successfully.',
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: 'psahmadtc@gmail.com',
                        subject: 'Security Scan Failed',
                        body: 'Security scan failed. Details in Logs.',
                        attachLog: true
                    )
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment using AWS...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment...'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment using AWS...'
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
