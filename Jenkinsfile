pipeline {
    agent { label "dev-server" }

    stages {
        stage('Hello DevOps') {
            steps {
                echo 'ALi Azhar DevOps Engineer'
            }
        }
        stage('Code Clone') {
            steps {
                echo 'This is code cloning from Github repo'
                git url: "https://github.com/muhammadaliazhar/NodeApp-CICD.git" , branch: "main"
                echo 'code clone successfully'
            }
        }
        stage('Build') {
            steps {
                echo 'This is building code using docker'
                sh "docker build -t todo-app ."
                echo 'Build successfully'
            }
        }
        stage("Push To DockerHub"){
            steps{
                withCredentials([usernamePassword(
                    credentialsId:"dockerHubCred",
                    usernameVariable:"dockerHubUser", 
                    passwordVariable:"dockerHubPass")]){
                sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}
                sh "docker image tag todo-app:latest ${env.dockerHubUser}/todo-app:latest"
                sh "docker push ${env.dockerHubUser}/todo-app:latest"
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
