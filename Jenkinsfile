pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-token', toolName: 'docker') {
                        sh "docker build -t 7845100317/checkoutservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-token', toolName: 'docker') {
                        sh "docker push 7845100317/checkoutservice:latest "
                    }
                }
            }
        }
    }
}
