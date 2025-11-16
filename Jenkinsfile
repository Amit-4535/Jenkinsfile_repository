

pipeline {
    agent any

    environment {
        DOCKERHUB_USER = 'amit4535'
        DOCKERHUB_REPO = 'myimage'
    }

    stages {

        stage('Creating image from container') {
            steps {
                sh 'docker commit container1 image:${BUILD_NUMBER}'
            }
        }

        stage('DockerHub Login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds',
                                                 usernameVariable: 'USER',
                                                 passwordVariable: 'PASS')]) {
                    sh 'echo "$PASS" | docker login -u "$USER" --password-stdin'
                }
            }
        }

        stage('Tag Image') {
            steps {
                sh 'docker tag image:${BUILD_NUMBER} ${DOCKERHUB_USER}/${DOCKERHUB_REPO}:${BUILD_NUMBER}'
            }
        }

        stage('Push Image to DockerHub') {
            steps {
                sh 'docker push ${DOCKERHUB_USER}/${DOCKERHUB_REPO}:${BUILD_NUMBER}'
            }
        }

    }
}

