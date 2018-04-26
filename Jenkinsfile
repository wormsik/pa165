pipeline {
	agent any

	environment {
		MY_IMG_NAME = "${DOCKER_REPO}/hsw-core"
		MY_FULL_TAG = "${MY_FULL_TAG}:${TAG}"
	}

	stages {
		stage('Build') {
			steps {
				echo 'building...'
			}
		}

		stage('Deployment') {
			steps {
				
				script {
					readFile('tags')
						.split('\n')
						.collect{ it.trim() }
						.collectEntries { [ it.split('\t')[0], it.split('\t')[1] ] }
						.findAll { it.value == "${TAG}" }
						.each {

							sh 'echo docker tag ${MY_FULL_TAG} ${MY_IMG_NAME}:${it.key}'
						}
				}
				
			}
		}
	}
}
