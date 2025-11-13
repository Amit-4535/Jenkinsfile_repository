
pipeline {
    agent any
    stages {
	stage('checkout stage'){
	  steps {
		git clone https://github.com/Amit-4535/Jenkinsfile_repository.git
}
}
	stage('build_Stage'){
	  steps {
		echo "build stage is running smoothly"
		sh 'mkdir -p build_stage'
		sh 'echo "build file is created and stored in the build_stage folder" > build_stage/build.txt' 
}
}
	stage('test_stage'){
	  steps {
		echo "test stage is running smoothly"
		sh 'mkdir -p test_stage'
		sh 'echo "test stage is running fine and the test file will be stored in the test_Stage folder" > test_stage/test.txt'
}
}
	stage('deploy_stage'){
	  steps {
		echo "deploy stage is running smoothly"
		sh 'mkdir -p deploy_stage'
		sh 'echo "deploy stage is running smoothly and deploy file is stored in the deploy_stage folder" > deploy_stage/deploy.txt'
}
}
}
}
