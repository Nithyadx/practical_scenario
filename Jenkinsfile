pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nithyadx/demo-app:1.0 .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub',
                    usernameVariable: 'USERNAME',
                    passwordVariable: 'PASSWORD'
                )]) {
                    sh 'docker login -u $USERNAME -p $PASSWORD'
                    sh 'docker push nithyadx/demo-app:1.0'
                }
            }
        }
    }
}

