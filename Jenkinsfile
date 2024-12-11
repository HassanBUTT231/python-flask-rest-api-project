pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'cloning the application'
                sh "whoami"
                git url : "https://github.com/HassanBUTT231/python-flask-rest-api-project.git", branch:"main"
                echo "successfully clones"
            }
        }
        stage('Build') {
            steps {
                echo 'building the application'
                sh "whoami"
                sh "docker build -t python-app ."
                echo "successfully build"
            }
        }
        stage('Pushing') {
            steps {
                echo 'Pushing image to dockerhub'
                withCredentials([usernamePassword(credentialsId: 'dockerHubCred', passwordVariable: 'dockerHubPass', usernameVariable: 'dockerHubUser')]) {
                sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                sh "docker tag python-app ${env.dockerHubUser}/python-app"
                sh "docker push ${env.dockerHubUser}/python-app"
                }

            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application'
                sh "docker compose down && docker compose up -d"
                echo "successfully build the application"
            }
        }
        
    }
}
