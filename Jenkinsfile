@Library("Shared") _
pipeline {
    agent { label 'vinod' }

    stages {

        stage("Code Clone") {
            steps {
                script {
                    code_checkout(
                        "https://github.com/AKASH1729/django-notes-app.git",
                        "main"
                    )
                }
            }
        }

        stage("Code Build & Test") {
            steps {
                script {
                    docker_build(
                        "notes-app",
                        "latest",
                        "akas11729"
                    )
                }
            }
        }

        stage("Push To DockerHub") {
            steps {
                script {
                    docker_push(
                        "notes-app",
                        "latest",
                        "akas11729"
                    )
                }
            }
        }

        stage("Deploy") {
            steps {
                script {
                    docker_compose()
                }
            }
        }
    }
}
