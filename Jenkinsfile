pipeline {
	agent any
	stages {
		
	stage('Build') {
		steps {	
		echo 'Building'
                sh 'docker-compose build buildsection'
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
                sh 'docker-compose build testsection'
				sh 'docker-compose up -d testsection'	
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
