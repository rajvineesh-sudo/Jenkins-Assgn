pipeline {
    agent none

    stages {

        stage('Checkout Code') {
            agent any
            steps {
                checkout scm
            }
        }

        stage('Deploy to TEST') {
            agent { label 'test' }
            steps {
                echo "Deploying to TEST node"
                sh '''
                rm -rf /opt/jenkins/test_app
                mkdir -p /opt/jenkins/test_app
                cp -r * /opt/jenkins/test_app/
                '''
            }
        }

        stage('Deploy to PROD') {
            agent { label 'prod' }
            when {
                expression { currentBuild.currentResult == 'SUCCESS' }
            }
            steps {
                echo "Deploying to PROD node"
                sh '''
                rm -rf /opt/jenkins/prod_app
                mkdir -p /opt/jenkins/prod_app
                cp -r * /opt/jenkins/prod_app/
                '''
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully: TEST → PROD"
        }
        failure {
            echo "Pipeline failed. PROD deployment skipped."
        }
    }
}
