pipeline {
	agent any

	stages {
		stage('install req') {
			steps {
				sh 'pip install -r requirements.txt'
			}
		}
		stage('run tests') {
			steps {
				sh 'python3 test.py'
			}
		}
	}
}
			