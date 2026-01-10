pipeline {
    agent any

    stages {
        stage('Pull Code to Folder') {
            steps {
                dir('develop_workspace') {
                    git branch: 'develop',
                        url: 'https://github.com/rajvineesh-sudo/Jenkins-Assgn.git'
                }
            }
        }

        stage('Verify Content') {
            steps {
                sh 'ls -l develop_workspace'
            }
        }
    }
}
