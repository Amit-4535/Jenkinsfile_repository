

pipeline {
   agent any
   stages {
/*   stage ('cloning the repo') {
	steps {
	  sh 'git clone https://github.com/Amit-4535/Jenkinsfile_repository.git'
*/
}
}
     stage ('pull the image from dockerhub') {
	steps {
	  sh 'docker pull ubuntu'
}
}
     stage ('creating the container from the image'){
	steps {
	  sh 'docker run -d --name container1 ubuntu'
}
}
}
}
