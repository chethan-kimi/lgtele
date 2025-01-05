pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git url: "https://github.com/chethan-kimi/lgtele.git", branch: 'development'
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
        stage('Deploy for testing'){
            when{
                branch 'development'
            }
            steps{
                input message: 'Is development complete?'
                echo 'development is complete and proceeding for testing'
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
                        "target": "development/"
                    },
                            {
                        "pattern": "README.md",
                        "target": "development/"
                    },
                            {
                        "pattern": "styles.css",
                        "target": "development/"
                    }
                        ]
                    }'''
                )
    }
    }
    }
    }
