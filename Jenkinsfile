pipeline {
    agent { label 'test' }

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Deploy to Test Server') {
            steps {
                sh '''
                rm -rf /opt/jenkins/test_app
                mkdir -p /opt/jenkins/test_app
                cp -r * /opt/jenkins/test_app/
                '''
            }
        }
    }
}
