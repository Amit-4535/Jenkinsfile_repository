


pipeline {
   agent any
   stages {
      stage ('installing apache2'){
	steps {
	  sh 'sudo apt-get update -y'
	  sh 'sudo apt-get upgrade -y'
	  sh 'sudo apt-get install apache2 -y'
}
} 
      stage ('installing docker'){
	steps {
	  sh 'sudo apt-get install docker.io -y '
}
}
}
}
