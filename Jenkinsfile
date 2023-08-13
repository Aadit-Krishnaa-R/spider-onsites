pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                docker build -t my-app .
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                docker run -p9000:80 -d --name app my-app
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhub-pwd')]) {
                    sh 'docker login -u aaditkrishnaar -p ${dockerhub-pwd}'
                }
                sh 'docker push aaditkrishnaar/jenkins-cicd'
            }
        }
    }
}