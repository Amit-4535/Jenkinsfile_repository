

pipeline{
   agent any
   stages{
     stage ('listing the containers'){
	steps {
	  sh 'docker ps -a'
}
}
     stage ('listing the images'){
	steps {
	  sh 'docker images -a'
}
}
     stage ('pull image from the registry'){
	steps {
	  sh 'docker pull ubuntu'
}
}
     stage ('creating container'){
	steps {
	  sh 'docker run -it --name container1 ubuntu /bin/bash'
}
}
}
}
