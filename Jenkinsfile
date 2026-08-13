@Library("Shared") _

pipeline {
    agent { label "Vinod" }

    stages {

        stage("Hello") {
            steps {
                script {
                    hello()
                }
            }
        }

        stage("code") {
            steps {
                script {
                    clone("https://github.com/preetkukreja556-beep/django-notes-app.git", "main")
                }
            }
        }

        stage("build") {
            steps {
                script {
                    docker_build("notes-app", "latest", "preetkukreja")
                }
            }
        }

        stage("Push to DockerHub") {
            steps {
                script {
                    docker_push("notes-app", "latest", "preetkukreja")
                }
            }
        }

        stage("deploy") {
            steps {
                echo "This is deploying the code"
                sh "docker compose up -d"
                }
            }
        }
    }
}
