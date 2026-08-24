pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Arunahugar534-sys/24-08-2026.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t my-app .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    kubectl apply -f deployment.yml
                    kubectl apply -f svc.yml
                '''
            }
        }
    }

    post {
        success {
            echo 'Deployment completed successfully'
        }

        failure {
            echo 'Deployment failed'
        }
    }
}
