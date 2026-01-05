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
                  docker_build("notes-app","1.1","amirshaikh993")
                }
            }
        }
        
        stage('Docker push') {
            steps {
                script{
                    docker_push("notes-app","1.1","amirshaikh993")
                }
            }
        }

        
        stage('Deploy on agnets docker container') {
            steps {
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
