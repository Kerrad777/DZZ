pipeline {
    agent any
    
    parameters {
        string(defaultValue: '', description: 'Student name', name: 'studentName')
    }
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Kerrad777/DZZ.git'
            }
        }
        
        stage('Build') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        
        stage('Run script') {
            steps {
                sh 'python hello.py --name ${params.studentName}'
            }
        }
        
        stage('Save output') {
            steps {
                sh 'echo $BUILD_OUTPUT > result.txt'
                archiveArtifacts artifacts: 'result.txt', onlyIfSuccessful: true
            }
        }
    }
}
