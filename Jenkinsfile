pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'docker build -t localhost:5000/html-pipeline:v1 .'
            }
        }
        stage('Push') {
            steps {
                bat 'docker push localhost:5000/html-pipeline:v1'
            }
        }
        stage('Deploy') {
            steps {
                bat 'docker rm -f html-pipeline-container || exit 0'
                bat 'docker run -d --name html-pipeline-container -p 8085:80 localhost:5000/html-pipeline:v1'
            }
        }
    }
}
