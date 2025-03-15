pipeline {
    agent any
    stages {
        stage('Checkout from github')
        steps {
            git branch: 'main', url: 'https://github.com/vpolachi/jenkins-java-cicd.git'
        }
    }
}
