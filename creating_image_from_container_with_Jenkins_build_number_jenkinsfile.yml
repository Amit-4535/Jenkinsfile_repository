pipeline {
    agent any

    stages {

        stage('Commit running container into image') {
            steps {
                // Commit the running container named "devcontainer"
                sh 'docker commit devcontainer devimage:${BUILD_NUMBER}'
                
                // Display message
                sh 'echo "Created new image: devimage:${BUILD_NUMBER}"'
            }
        }

        stage('List all images') {
            steps {
                sh 'docker images | grep devimage'
            }
        }

        stage('Success message') {
            steps {
                sh 'echo "Image creation from container completed successfully!"'
            }
        }

    }
}

