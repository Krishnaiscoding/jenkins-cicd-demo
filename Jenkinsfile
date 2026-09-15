pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Building Application...'
                sh 'ls -la'
            }
        }
        stage('Test') {
            steps {
                echo 'Running Tests...'
                sh 'test -f index.html'
            }
        }
        stage('Docker Build') {
            steps {
                echo 'Building Docker Image ...'
                sh 'docker build -t krishnaiscoding/jenkins-demo:latest .'
            }
        }
        stage('Docker Push') {
            steps {
                echo 'Pushing Docker Image ...'
                sh 'docker push krishnaiscoding/jenkins-demo:latest'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying Application ...'
                sh 'docker run -d -p 8080:80 krishnaiscoding/jenkins-demo:latest'
            }
        }
    }
}