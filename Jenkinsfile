

pipeline {
   agent any
   stages {
      stage ('cloning repo'){
	steps {
	  sh 'git clone https://github.com/Amit-4535/Jenkinsfile_repository.git'
}
}

      stage ('list containers'){
	steps {
	  sh 'docker ps -a'
}
}
      stage ('list the images'){
	steps {
	  sh 'docker images -a'
}
}
      stage ('success message') {
	steps {
	  sh 'echo "above all the commands and jenkinsfile is much cleaner"'
}
}
}
}
