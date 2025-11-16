

pipeline {
   agent any
   stages {
/*   stage ('cloning the repo') {
	steps {
	  sh 'git clone https://github.com/Amit-4535/Jenkinsfile_repository.git'

}
}
*/
     stage ('pull_the_image_from_dockerhub') {
	steps {
	  sh 'docker pull ubuntu'
}
}
     stage ('creating_the_container_from_the_image'){
	steps {
	  sh 'docker run -d --name container1 ubuntu'
}
}
}
}
