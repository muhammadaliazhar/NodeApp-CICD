pipeline {
    agent { label "agent-1" }

    stages {
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
                sh "docker build -t node-app ."
                echo 'Build successfully'
            }
        }
        stage('Test') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Deploy') {
            steps {
                echo 'This is node-app deployment stage'
                sh "docker run -d -p 8000:8000 node-app:latest"
                echo 'Node app successfully deployed on docker container which runs on agent machine'
            }
        }
    }
}
