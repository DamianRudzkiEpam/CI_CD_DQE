pipeline {
	agent any

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
		stage('echo') {
            steps {
            	echo 'Deploying'
            }
		}
	}
}
			