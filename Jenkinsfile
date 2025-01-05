pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git url: "https://github.com/chethan-kimi/lgtele.git", branch: 'master'
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
                branch 'master'
            }
            steps{
                input message: 'Is Testing successful?'
                echo 'Testing is successful and deploying for Production'
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
                        "target": "master/"
                    },
                            {
                        "pattern": "README.md",
                        "target": "master/"
                    },
                            {
                        "pattern": "styles.css",
                        "target": "master/"
                    }
                        ]
                    }'''
                )
    }
    }
    }
    }
