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
                    git config user.name 'DamianRudzkiEpam'
                    git config user.email 'damian_rudzki@epam.com'
                    git remote add origin git@github.com:DamianRudzkiEpam/CI_CD_DQE.git
                    git fetch --all
                    git checkout $BRANCH_NAME
                    git checkout develop
                    git merge $BRANCH_NAME
                    git push origin develop
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