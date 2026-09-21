pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'docker build -t devops-demo:v1 .'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing application...'
                sh 'docker images devops-demo:v1'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'

                sh '''
                    docker stop devops-demo || true
                    docker rm devops-demo || true
                    docker run -d --name devops-demo -p 3000:3000 devops-demo:v1
                '''
            }
        }
    }
}
