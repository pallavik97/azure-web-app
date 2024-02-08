pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'your-git-credentials-id', url: 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('your-docker-image-name:tag', './docker')
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
