pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                sudo docker build -t my-app .
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                sudo docker run -p9000:80 -d --name app my-app
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
}