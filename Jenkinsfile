pipeline {
	agent any
	environment {
        DOCKERHUB_CREDENTIALS= credentials('lab07')
    }
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
				sh 'docker-compose up -d buildsection'
				echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin
		docker tag buildsection:latest yivess/lab07
		docker push yivess/lab07
            }
            post {
		always{
		    sh 'docker logout'
		}
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
