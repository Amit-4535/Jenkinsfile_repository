
pipeline {
    agent any

    stages {
        stage('check docker access') {
            steps {
                sh 'docker ps'
                echo "✅ Docker is accessible to Jenkins"
            }
        }

        stage('list containers') {
            steps {
                sh 'docker ps -a'
            }
        }

        stage('list images') {
            steps {
                sh 'docker images -a'
            }
        }

        stage('pull ubuntu image') {
            steps {
                sh 'docker pull ubuntu'
            }
        }

        stage('run container') {
            steps {
                sh 'docker run -d --name container1 ubuntu sleep 60'
            }
        }
    }
}

