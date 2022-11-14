pipeline {
	agent any
	
	stages {
		stage('Test') {
			steps {
				sh 'python3 -m unittest -v tests.py'
			}
		}
        stage('Merge to develop') {
			steps {
				git checkout develop
				git pull origin develop
				git merge $BRANCH_NAME
			}
		}
	}
}
			