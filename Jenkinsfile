

pipeline {
    agent any

    environment {
        DOCKERHUB_USER = 'amit4535'
        DOCKERHUB_REPO = 'myimage'
    }

    stages {

        stage('DockerHub Login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds',
                                                 usernameVariable: 'USER',
                                                 passwordVariable: 'PASS')]) {
                    sh 'echo "$PASS" | docker login -u "$USER" --password-stdin'
                }
            }
        }

        stage('Pull Image') {
            steps {
                sh 'docker pull ${DOCKERHUB_USER}/${DOCKERHUB_REPO}:${BUILD_NUMBER}'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f newcontainer || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh '''
                docker run -d --name newcontainer \
                ${DOCKERHUB_USER}/${DOCKERHUB_REPO}:${BUILD_NUMBER}
                '''
            }
        }

    }
}

