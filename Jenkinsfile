pipeline{
    agent any
    tools{
        maven 'mvn3.9.9' // Use the Maven installation configured in Jenkins
    }
    environment{
        SONAR_AUTH_TOKEN = credentials('jenkins-token') // Inject SonarQube token as an environment variable
    }
    stages{
        stage("Checkout"){
            steps{
                checkout scm
            }
        }
        stage("Debug Token"){
            steps{
                echo "SonarQube Token: $SONAR_AUTH_TOKEN" // Debug step to verify the token
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
        stage("SonarQube Analysis"){
            steps{
                withSonarQubeEnv('SonarQube-Server') { // Use the SonarQube server configured in Jenkins
                    sh 'mvn sonar:sonar -Dsonar.projectKey=my-project -Dsonar.projectName="My Project" -Dsonar.host.url=http://43.205.96.24:9000 -Dsonar.login=$SONAR_AUTH_TOKEN'
                }
            }
        }
    }
    post{
        success{
            echo "Pipeline succeeded! SonarQube analysis completed."
        }
        failure{
            echo "Pipeline failed. Check the logs for details."
        }
    }
}
