pipeline {
    agent any

    environment {
        // Define environment variables
        DOCKER_IMAGE = "your-docker-registry/your-app-name"
        KUBERNETES_NAMESPACE = "your-namespace"
        KUBERNETES_DEPLOYMENT_NAME = "your-deployment-name"
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from version control
                git 'https://your-repo-url.git'
            }
        }

        stage('Build') {
            steps {
                // Build the Spring Boot application
                sh './mvnw clean package'
            }
        }

        stage('Docker Build') {
            steps {
                // Build Docker image
                script {
                    docker.build("${DOCKER_IMAGE}:${env.BUILD_NUMBER}")
                }
            }
        }

        stage('Docker Push') {
            steps {
                // Push Docker image to the registry
                script {
                    docker.withRegistry('https://your-docker-registry', 'your-credentials-id') {
                        docker.image("${DOCKER_IMAGE}:${env.BUILD_NUMBER}").push()
                    }
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                // Deploy the application to Kubernetes
                script {
                    sh """
                    kubectl set image deployment/${KUBERNETES_DEPLOYMENT_NAME} \
                    -n ${KUBERNETES_NAMESPACE} \
                    ${KUBERNETES_DEPLOYMENT_NAME}=${DOCKER_IMAGE}:${env.BUILD_NUMBER}
                    """
                }
            }
        }

        stage('Clean Up') {
            steps {
                // Clean up old Docker images (optional)
                sh "docker rmi ${DOCKER_IMAGE}:${env.BUILD_NUMBER}"
            }
        }
    }

    post {
        success {
            echo 'Deployment was successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}

