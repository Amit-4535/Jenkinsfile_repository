

pipeline {
    agent any

    parameters {
        string(name: 'IMAGE_TAG', defaultValue: 'latest', description: 'Tag to deploy')
    }

    environment {
        DOCKERHUB_USER = "amit4535"
        DOCKERHUB_REPO = "myimage"
    }

    stages {

        stage('Pull Image from Docker Hub') {
            steps {
                sh "docker pull ${DOCKERHUB_USER}/${DOCKERHUB_REPO}:${IMAGE_TAG}"
            }
        }

        stage('Run Container') {
            steps {
                sh """
                    docker rm -f mycontainer || true
                    docker run -d --name mycontainer ${DOCKERHUB_USER}/${DOCKERHUB_REPO}:${IMAGE_TAG}
                """
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'docker ps'
            }
        }
    }
}

