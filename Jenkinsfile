pipeline {
	agent any
	stages {
		
	stage('Build') {
		steps {	
		echo 'Building'
                sh 'docker-compose build build-agent'
				sh 'docker-compose up -d test-agent'	
            }
            post {
                failure {
                    echo 'ERROR IN Building'
                    sh 'false'
                }
                success {
                    echo 'SUCCESS IN Building'
                }
            }
        }
	
	stage('Test') {
		steps {	
		echo 'Testing'
                sh 'docker-compose build test-agent'
				sh 'docker-compose up -d test-agent'	
            }
            post {
                failure {
                    echo 'ERROR IN TESTING'
                    sh 'false'
                }
                success {
                    echo 'SUCCESS IN TESTING'
                }
            }
        }
    }
}
