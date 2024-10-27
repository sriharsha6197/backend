pipeline {
    agent { label 'terraform'}
    stages {
        stage('download dependencies'){
            steps {
                echo "download dependenciees"
                sh 'npm install'
                sh 'env'
            }
        }
        stage('Code compile'){
            when {
              allOf {
                expression { env.TAG_NAME != env.GIT_BRANCH}
                branch 'main'
              }
            }
            steps {
                echo "Code compile"
            }
        }
        stage('code unit tests'){
            when {
              allOf {
                expression { env.TAG_NAME != env.GIT_BRANCH}
                branch 'main'
              }
            }
            steps {
                echo "unit tests"
            }
        }
        stage('Code quality checks'){
            when {
              allOf {
                expression { env.TAG_NAME != env.GIT_BRANCH}
              }
            }
            steps {
                echo "Code quality checks"
                sh 'sonar-scanner -Dsonar.projectKey=backend -Dsonar.host.url=http://172.31.17.88:9000 -Dsonar.login=admin -Dsonar.password=harsha123 -Dsonar.qualitygate.wait=true'
            }
        }
        stage('Code deploy'){
            when {
                expression { env.TAG_NAME ==~ ".*"}
            }
            input {
                message "Should we continue?"
            }
            steps {
                echo "Code deploy"
            }
        }
    }
}