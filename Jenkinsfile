pipeline{
    agent any
       tools{
          maven 'mvn3.9.9' // Use the Maven installation configured in Jenkins   
       }
    stages{
        stage("Checkout"){
            steps{
               checkout scm
            }
        }
        stage("Unit Testing"){
            steps{
               sh 'mvn test'
            }
        }
        stage("Maven Build"){
            steps{
               sh 'mvn clean package'
            }
        }
    }
}
