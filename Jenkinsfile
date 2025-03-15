pipeline {
    agent any
    stages {
        stage('Checkout from github')
        steps {
            ggit branch: 'main', url: 'https://github.com/vpolachi/jenkins-java-cicd.git'
        }
    }
}
