pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/pallavik97/azure-web-app'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('pkdocker:latest', './docker')
                }
            }
        }

        stage('Terraform Apply') {
            steps {
                script {
                    dir('terraform') {
                        sh 'terraform init'
                        sh 'terraform apply -auto-approve'
                    }
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    sh 'kubectl apply -f ./kubernetes/deployment.yaml'
                }
            }
        }
    }

    post {
        always {
            // Clean up after the pipeline finishes
        }
    }
}
