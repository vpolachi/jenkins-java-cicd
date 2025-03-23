pipeline{
    agent any
        tools{
            maven 'maven3.9.9'
        }
    stages{
        stage("Checkout"){
            steps{
                checkout scm
            }
        }
        stage("maven build"){
            steps{
                sh 'mvn clean package'
            }
        }
    }
}
