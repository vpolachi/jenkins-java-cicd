pipeline{
    agent any

     environment{
        SONAR_SCANNER_HOME = tool name: 'SonarQube-Scanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
    }
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
        stage('SonarQube Analysis'){
            steps{
                withSonarQubeEnv('SonarQube-Server'){ // Use the name configured in Jenkins
                    sh "${SONAR_SCANNER_HOME}/bin/sonar-scanner -Dsonar.projectKey=your-project-key -Dsonar.sources=. -Dsonar.host.url=http://172.31.45.100:9000 -Dsonar.login=your-sonarqube-token"
                }
            }
        }
    }
}
