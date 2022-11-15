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
    		branch 'feature*'
    	}
    	steps {
        	sh 'git checkout develop'
			sh 'git pull origin develop'
			sh 'git merge $BRANCH_NAME'
    	}
	}
	stage('echo') {
		steps {
		echo 'Deploying'
            }
		}
	}
}