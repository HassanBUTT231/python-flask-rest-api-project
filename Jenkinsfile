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
    }
}
