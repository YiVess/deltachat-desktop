pipeline {
	agent any
	stages {
		stage('Test') {
			steps {
				echo 'Testing'
				sh 'docker-compose build'
						sh 'docker-compose up'
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