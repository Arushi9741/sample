pipeline{
    agent any
    stages{
        stage('clone repo'){
            steps{
                git credentialsId : "Demotoken", url:"https://github.com/Arushi9741/sample.git", branch:"main"
            }
        }
        stage('Dependency'){
            steps{
                bat '''
                python -m venv  venv
                call venv\\Script\\activate
                python -m pip install --upgrade pip
                pip install pytest
                '''
            }
        }
        stage('test'){
            steps{
                bat '''
                call venv\\Script\\activate
                pytest testpy
                '''
            }
        }
        stage('deploy'){
            steps{
                bat '''
                call venv\\Script\\activate
                python stack.py
                '''
            }
        }

    }
    post{
        success{
            echo "pipeline success"
        }
        failure{
            echo "pipeline failure"
        }
    }
}

