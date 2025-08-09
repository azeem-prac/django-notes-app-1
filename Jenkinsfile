 @Library('Shared') _
pipeline {
    agent { label "Agent" }

    stages {
        stage('Clone') {
            steps {
                script{
                clone("https://github.com/azeem-prac/django-notes-app-1.git","main")
            }
        }
        }
        stage('Build-image') {
            steps {
                script{
                docker_build("notes-app","latest","azeem501")
                }
            }
        }
        stage('Push-image') {
            steps {
                script{
                    docker_push("notes-app","latest","azeem501")
                }
            }
        }
        stage('Deploy') {
            steps {
                sh "docker-compose down && docker-compose up -d"
            }
        }
     
    }
}
