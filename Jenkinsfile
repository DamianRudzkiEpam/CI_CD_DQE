pipeline {
	agent any

	//when feature branch:
	// -tests
	// -if ok, merge to develop


	stages {
        stage('Test') {
            when {
                branch 'feature/*'
            }
            steps {
                sh 'python3 -m unittest -v tests.py'
            }
		}
        stage('Merge to develop') {
            when {
                branch 'feature/*'
            }
			steps {
				git checkout develop
				git pull origin develop
				git merge $BRANCH_NAME
			}
		}
	}
}
			