pipeline{
    agent any
    stages{
        stage("Checkout from GitHub"){
            steps{
                git branch: 'main', url: 'https://github.com/vpolachi/jenkins-java-cicd.git'
            }
        }
    }

}
