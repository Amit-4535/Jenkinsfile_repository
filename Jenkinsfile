pipeline {
    agent any

    environment {
        DOCKERHUB_USER = 'amit4535'
        DOCKERHUB_REPO = 'myimage'
        IMAGE_TAG = 'latest'
    }

    stages {

        stage('Pull Image from Docker Hub') {
            steps {
                script {
                    echo "Pulling image: ${DOCKERHUB_USER}/${DOCKERHUB_REPO}:${IMAGE_TAG}"
                    sh """
                        docker pull ${DOCKERHUB_USER}/${DOCKERHUB_REPO}:${IMAGE_TAG}
                    """
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    echo "Running container from image..."

                    // Stop & remove existing container if present
                    sh """
                        if [ \$(docker ps -aq -f name=mycontainer) ]; then
                            docker rm -f mycontainer
                        fi
                    """

                    // Run new container
                    sh """
                        docker run -d --name mycontainer ${DOCKERHUB_USER}/${DOCKERHUB_REPO}:${IMAGE_TAG}
                    """
                }
            }
        }

        stage('Verify Container') {
            steps {
                script {
                    echo "Listing running containers..."
                    sh "docker ps"
                }
            }
        }
    }
}

