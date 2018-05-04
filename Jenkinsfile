pipeline {
	agent any

	environment {
		MY_IMG_NAME = "${DOCKER_REPO}/hsw-core"
		MY_FULL_TAG = "${MY_IMG_NAME}:${TAG}"
	}

	stages {
		stage('Build') {
			steps {
				echo 'building...' + (env.test.toBoolean() ? 'test' : 'nic') + ' - ' +env.test
			}
		}

		stage('Deployment') {
			steps {
				
				script {
					readFile('tags')
						.split('\n')
						.collect { it.trim() }
						.findAll { it.length() > 0 }
						.collectEntries { [ it.split()[0], it.split()[1] ] }
						.findAll { it.value == "${TAG}" }
						.each {
							sh "echo docker tag ${MY_FULL_TAG} ${MY_IMG_NAME}:${it.key}"
						}
				}
				
			}
		}
	}
}
