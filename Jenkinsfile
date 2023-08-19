pipeline {
    agent any

    triggers {
        pollSCM('*/2 * * * *')
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Kerrad777/DZZ.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Script') {
            steps {
                sh 'python hello.py --name Yura > result.txt'
            }
        }

        stage('Save Result as Artifact') {
            steps {
                archiveArtifacts artifacts: 'result.txt', onlyIfSuccessful: true
            }
        }
    }
}
