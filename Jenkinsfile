pipeline {
    agent any
    environment {
        EMAIL_RECIPIENT = "psahmadtc@gmail.com"
        }
    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing the code...'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment...'
            }
        }
        stage('Complete') {
            steps {
                echo 'Completed!'
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
        always {
            //mail bcc: '', body: 'Pipeline execution status: ${currentBuild.currentResult} \nLogs attached.' ,
              //   subject: "Jenkins Pipeline Update",
                // to: 'psahmadtc@gmail.com'
            emailext(
            to: "${EMAIL_RECIPIENT}",
            subject: "Unit and Integration Tests Failed",
            body: "The Unit and Integration Tests Have Failed. Please check the attached logs for details.",
          //  attachmentsPattern: 'test-*.log',
            attachLog: true
          )
        }
    }
}
