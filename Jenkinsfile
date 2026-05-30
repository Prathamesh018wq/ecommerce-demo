pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/Prathamesh018wq/ecommerce-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ecommerce-app:v2 .'
            }
        }

        stage('Push To ECR') {
            steps {
                sh '''
                aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 660405908881.dkr.ecr.ap-south-1.amazonaws.com

                docker tag ecommerce-app:v2 660405908881.dkr.ecr.ap-south-1.amazonaws.com/ecommerce-app:v2

                docker push 660405908881.dkr.ecr.ap-south-1.amazonaws.com/ecommerce-app:v2
                '''
            }
        }
    }
}
