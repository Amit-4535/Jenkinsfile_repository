

pipeline {
    agent any

    environment {
        DOCKERHUB_USER = 'amit4535'
        DOCKERHUB_REPO = 'myimage'
        IMAGE_TAG = "${BUILD_NUMBER}"
    }

    stages {

        stage('Create Image from Container') {
            steps {
                sh "docker commit container1 ${DOCKERHUB_USER}/${DOCKERHUB_REPO}:${IMAGE_TAG}"
            }
        }

        stage('Login to DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds',
                                                 usernameVariable: 'USER',
                                                 passwordVariable: 'PASS')]) {
                    sh "echo $PASS | docker login -u $USER --password-stdin"
                }
            }
        }

        stage('Push Image') {
            steps {
                sh "docker push ${DOCKERHUB_USER}/${DOCKERHUB_REPO}:${IMAGE_TAG}"
            }
        }

        stage('Trigger Deploy Job') {
            steps {
                build job: 'Deploy_Docker_Image',
                      parameters: [
                        string(name: 'IMAGE_TAG', value: "${IMAGE_TAG}")
                      ]
            }
        }
    }
}

