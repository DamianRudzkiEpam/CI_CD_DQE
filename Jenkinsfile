pipeline {
	agent any
	
	stages {
		stage('Test') {
			steps {
				python -m unittest -v tests.py
			}
		}
	}
}
			