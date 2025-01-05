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
                branch 'us-1234'
            }
            steps{
                input message: 'Is test successful?'
                echo 'Test is successful and proceeding for development'
            }
        }
                stage('Upload to JFrog Artifactory') {
            steps {
                rtServer (
                    id: 'Artifactory-Server',
                    url: 'https://trial116ruw.jfrog.io/artifactory/ts-lgtele/',
                    credentialsId: 'Jfrog'
                )
                rtUpload (
                    serverId: 'Artifactory-Server',
                    spec: '''{
                        "files": [
                            {
                        "pattern": "file1.txt",
                        "target": "us-1234/"
                    },
                                                {
                        "pattern": "README.md",
                        "target": "us-1234/"
                    },
                            {
                        "pattern": "Jenkinsfile",
                        "target": "us-1234/"
                    }
                        ]
                    }'''
                )
    }
    }
