

pipeline {
    agent any

    stages {

        stage('Pull image from Docker Hub') {
            steps {
                sh 'docker pull ubuntu:latest'
                /* You can replace "ubuntu:latest" with your own image 
                   example: docker pull amit4535/myimage:latest 
                */
            }
        }

        stage('Create container from pulled image') {
            steps {
                sh 'docker run -d --name mycontainer ubuntu:latest sleep infinity'
                /* 
                - Use -d (detached mode) because Jenkins cannot use -it
                - sleep infinity keeps the container running in background
                */
            }
        }

        stage('List containers') {
            steps {
                sh 'docker ps -a'
            }
        }

        stage('List images') {
            steps {
                sh 'docker images -a'
            }
        }

        stage('Success message') {
            steps {
                sh 'echo "Image pulled and container created successfully!"'
            }
        }

    }
}

