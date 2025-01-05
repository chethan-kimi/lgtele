pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git url: "https://github.com/chethan-kimi/lgtele.git", branch: 'testing'
            }
        }
        stage('Verify Files') {
            steps {
                sh 'ls -la'
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
        stage('Deploy for Production'){
            when{
                branch 'testing'
            }
            steps{
                input message: 'Is test successful?'
                echo 'Test is successful and proceeding for Production'
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
                        "target": "testing/"
                    },
                            {
                        "pattern": "README.md",
                        "target": "testing/"
                    },
                            {
                        "pattern": "styles.css",
                        "target": "testing/"
                    }
                        ]
                    }'''
                )
    }
    }
    }
    }
