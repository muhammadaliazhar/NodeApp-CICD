@Library("shared") _ 
pipeline {
    agent { label "dev-server" }

    stages {
        stage('Welcome') {
            steps {
                script{
                    hello()
                }
            }
        }
        stage('Code Clone') {
            steps {
                script{
                     clone("https://github.com/muhammadaliazhar/NodeApp-CICD.git","main")
                }
            }
        }
        stage('Build') {
            steps {
                script{
                    docker_build("todo-app","latest","maliazhar")
                }
            }
        }
        stage("Push To DockerHub"){
            steps{
                script{
                    docker_push("todo-app","latest","maliazhar")
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'This is node-app deployment stage'
                sh "docker compose down && docker compose up -d"
                echo 'Node app successfully deployed on docker container which runs on agent machine'
            }
        }
    }
}
