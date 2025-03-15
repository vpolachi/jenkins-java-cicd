pipeline{
    agent any
    stages{
        stage("Checkout from GitHub"){
            steps{
                git branch: 'main', url: 'https://github.com/vpolachi/jenkins-java-cicd.git'
            }
        }
        stage("maven Build"){
            steps{
                sh 'mvn test'
            }
        }
        stage("maven Build"){
            steps{
                sh 'mvn clean package'
            }
        }
    }

}

