pipeline{
    agent any
    stages{
        stage("Checkout"){
            steps{
               checkout scm
            }
        stage("Unit Testing"){
            steps{
               sh 'mvn test'
            }
        }
    }
}
