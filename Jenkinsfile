pipeline {
    agent { label 'prod' }

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Deploy to Prod Server') {
            steps {
                sh '''
                rm -rf /opt/jenkins/prod_app
                mkdir -p /opt/jenkins/prod_app
                cp -r * /opt/jenkins/prod_app/
                '''
            }
        }
    }
}
