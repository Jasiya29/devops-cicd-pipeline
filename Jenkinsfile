pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t devops-cicd:v1 .'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing application...'
                sh 'docker run --rm devops-cicd:v1 node -e "console.log(\'Test passed\')"'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'

                sh '''
                    docker stop devops-cicd || true
                    docker rm devops-cicd || true
                    docker run -d --name devops-cicd -p 3000:3000 devops-cicd:v1
                '''
            }
        }
    }
}
