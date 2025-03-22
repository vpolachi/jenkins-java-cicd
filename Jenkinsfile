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
        stage("OWASP Dependency-Check Analysis") {
            steps {
              // Run Dependency-Check scan on the target directory and save reports to ./reports
                dependencyCheck additionalArguments: '--scan ./target --format ALL --project MypetclinicProject --out ./reports', odcInstallation: 'dependency-check'
                
                // Publish Dependency-Check results to Jenkins
                dependencyCheckPublisher pattern: '**/reports/dependency-check-report.xml'
            }
        }
    }
}
