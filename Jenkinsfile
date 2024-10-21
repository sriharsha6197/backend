pipeline {
    agent { label 'terraform'}
    stages{
        stage('download dependencies'){
            steps{
                echo "download dependencies"
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
            }
        }
        stage('Code deploy'){
            steps{
                echo "Code deploy"
            }
        }
    }
}