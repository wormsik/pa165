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
				var str = readFile('tags')
				echo str
			}
		}
	}
}
