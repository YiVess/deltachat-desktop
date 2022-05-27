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
	stage('Deploy') {
		steps {
                echo 'Deploying'
                archiveArtifacts(artifacts: '**/*.txt', followSymlinks: false)
                sh 'docker-compose build deploysection'
				sh 'docker-compose up -d deploysection'
            }
            post {
                failure {
                    echo 'ERROR IN DEPLOYING'
                    sh 'false'
                }
                success {
                    echo 'SUCCESS IN DEPLOYING'
                }
            }
        }
    }
}
