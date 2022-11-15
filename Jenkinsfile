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
                sh '''
                    git fetch --all
                    git checkout $BRANCH_NAME
                    git checkout develop
                    git merge $BRANCH_NAME
                '''
            }
        }
        stage('Deploy to NONPROD') {
            when {
                branch 'release/*'
            }
            steps {
                echo 'Deploying TO NONPROD....'
            }
        }

        stage('Deploy to PROD') {
            when {
                branch 'master'
            }
            steps {
                echo 'Deploying TO PROD....'
            }
        }
    }
}