@Library('Jenkins-Shared-Libraries') _
pipeline {
    agent {label "agent-jenkins"}

    stages {
        stage('Clone') {
            steps {
                script{
                  echo "Cloning code from github"
                  clone("https://github.com/AmirShaikhAws/django-notes-app.git", "main")
                }
            }
        }
        stage('docker build') {
            steps {
                script{
                  docker_build("notes-app","latest","amirshaikh993")
                }
            }
        }
        
        stage('Docker push') {
            steps {
                script{
                    docker_push("notes-app","latest","amirshaikh993")
                }
            }
        }

        
        stage('deploy') {
            steps {
                sh "docker rm -f notes-app || true"
                sh 'docker run -d -p 8000:8000 --name notes-app notes-app:latest'
                sh "docker ps"
            }
        }
    }
}
