pipeline {
    agent any

    stages {
        stage('Build and Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DOCKERHUB_CREDENTIALS', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    script {
                        // List files in the build directory to confirm location
                        sh 'ls -la build'

                        // Use relative path to deploy.sh and ensure it's executable
                        sh 'chmod +x build/deploy.sh'
                        sh '.deploy.sh'
                    }
                }
            }
        }
    }
}
