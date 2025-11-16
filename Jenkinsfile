

pipeline {
    agent any

    environment {
        DOCKER_USER = "amit4535"
        IMAGE_NAME = "myimage"
        IMAGE_TAG = "15"    // <--- FIXED: this must be defined
    }

    stages {

        stage('Pull Image from DockerHub') {
            steps {
                echo "Pulling image: ${DOCKER_USER}/${IMAGE_NAME}:${IMAGE_TAG}"
                sh "docker pull ${DOCKER_USER}/${IMAGE_NAME}:${IMAGE_TAG}"
            }
        }

        stage('Stop Old Container') {
            steps {
                echo "Stopping old container if exists..."
                sh """
                    if [ \$(docker ps -aq -f name=newcontainer) ]; then
                        docker stop newcontainer || true
                        docker rm newcontainer || true
                    fi
                """
            }
        }

        stage('Run New Container') {
            steps {
                echo "Running new container..."
                sh "docker run -d --name newcontainer -p 8080:80 ${DOCKER_USER}/${IMAGE_NAME}:${IMAGE_TAG}"
            }
        }

        stage('Verify Deployment') {
            steps {
                sh "docker ps -a"
            }
        }
    }
}

