pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git url: "https://github.com/chethan-kimi/lgtele.git"
            }
        }
        stage('Build Application') {
            steps {
                echo 'Build Application'
            }
        }
        stage('Package Application') {
            steps {
                echo 'Package Application'
            }
        }
        stage('Deploy for development'){
            when{
                branch 'development'
            }
            steps{
                input message: 'Is development successful?'
                echo 'development is successful and proceeding for testing'
            }
        }
    }
    }
