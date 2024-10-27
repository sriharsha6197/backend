pipeline {
    agent { label 'terraform'}
    stages{
        stage('download dependenciees'){
            steps{
                echo "download dependenciees"
                sh 'npm install'
            }
        }
        stage('Code test'){
            steps{
                echo "Code test"
            }
        }
        stage('Code quality checks'){
            steps{
                echo "Code quality checks"
                sh 'sonar-scanner -Dsonar.projectKey=backend -Dsonar.host.url=http://172.31.17.88:9000 -Dsonar.login=admin -Dsonar.password=harsha123 -Dsonar.qualitygate.wait=true'
            }
        }
        stage('Code deploy'){
            input{
                message "Should we continue?"
            }
            steps{
                echo "Code deploy"
            }
        }
    }
}