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
	stage('myConditionalStage') {
    	when {
        	branch 'myBranch'
    	}
    	steps {
        	echo 'triggered by myBranch'
    	}
	}
	stage('echo') {
		steps {
		echo 'Deploying'
            }
		}
	}
}
			