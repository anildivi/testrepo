pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/yourname/project.git'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t my-nginx-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f nginx-container || true

                docker run -d \
                --name nginx-container \
                -p 80:80 \
                my-nginx-app
                '''
            }
        }
    }
}
