pipeline {
    agent any

    parameters {
        string(name: 'IMAGE_TAG', defaultValue: '', description: 'Tag of the image to deploy')
    }

    environment {
        DOCKERHUB_USER = 'amit4535'
        DOCKERHUB_REPO = 'myimage'
    }

    stages {

        stage('Pull Image from DockerHub') {
            steps {
                echo "Pulling image: ${DOCKERHUB_USER}/${DOCKERHUB_REPO}:${IMAGE_TAG}"
                sh "docker pull ${DOCKERHUB_USER}/${DOCKERHUB_REPO}:${IMAGE_TAG}"
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                    if docker ps -a --format '{{.Names}}' | grep -w newcontainer; then
                        docker stop newcontainer || true
                        docker rm newcontainer || true
                    fi
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh """
                    docker run -d --name newcontainer ${DOCKERHUB_USER}/${DOCKERHUB_REPO}:${IMAGE_TAG}
                """
            }
        }

        stage('Verify Deployment') {
            steps {
                sh "docker ps -a | grep newcontainer"
            }
        }

    }
}

