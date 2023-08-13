pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                docker build -t aaditkrishnaar/jenkins-cicd .
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                docker run -p9000:80 -d --name app1 aaditkrishnaar/jenkins-cicd
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh 'docker login -u aaditkrishnaar -p @ngryB1rd'
                // sh 'docker tag my-app aaditkrishnaar/jenkins-cicd'
                sh 'docker push aaditkrishnaar/jenkins-cicd'
            }
        }
    }
}