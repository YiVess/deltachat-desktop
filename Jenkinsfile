pipeline {
	agent any
	stages {
		stage('Test') {
			steps {
				
                sh 'docker-compose build'
				sh 'docker-compose up'
            }
            post {
                failure {
                    echo 'ERROR IN TESTING - Job ${env.JOB_NAME} build ${env.BUILD_NAME}'
                    sh 'false'
                }
                success {
                    echo 'SUCCESS IN TESTING - Job ${env.JOB_NAME} build ${env.BUILD_NAME}'
                }
            }
        }
    }
}
