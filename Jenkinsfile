pipeline{
    agent any
    stages{
        stage('clone repo'){
            steps{
                git credentialsId : "Demotoken", url : 'https://github.com/RakhiGpt/jen.git' , branch : 'main'
            }

        }
        stage('dependency'){
            steps{
                bat '''
                python -m venv venv
                call venv\\Script\\active
                pip install --upgrade pip
                pip install pytest
                '''
            }

        }
        stage('test'){
            steps{
                bat '''
                call venv\\Script\\active
                pytest test.py
                '''
            }
        }
        stage('deploy'){
            steps{
                bat '''
                call venv\\Script\\active
                python hello.py
                '''
            }
        }
    }
    post{
        success {
            echo "pipeline success"
        }
        failure {
            echo "pipeline failures"
        }
    }
}


