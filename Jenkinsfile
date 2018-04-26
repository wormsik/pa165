pipeline {
	agent any

	environment {
		MY_FULL_TAG = "${DOCKER_REPO}/hsw-core:${TAG}"
	}

	stages {
		stage('Build') {
			steps {
				echo 'building...'
			}
		}

		stage('Deployment') {
			steps {
				
				script {readFile('tags').split('\n').collect{ it.trim() }.collectEntries {
					[ it.split('\t')[0], it.split('\t')[1] ]
				}.findAll { it.value == '3.0' }.each {
					echo 'selecting ' + it.key
				}
				}
				
			}
		}
	}
}
