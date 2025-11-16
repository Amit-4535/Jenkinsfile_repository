


pipeline {
    agent any
    stages {
      stage ('creating the image from the container'){
	steps {
	  sh 'docker commit container1 image:${BUILD_NUMBER}'
}
}   
}
}
