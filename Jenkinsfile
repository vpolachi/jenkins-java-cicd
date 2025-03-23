pipeline{
    agent any
        tools{
            maven 'maven3.9.9'
            hudson.plugins.sonar.SonarRunnerInstallation 'sonar-scanner'
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
         stage("SonarQube Analysis"){
            steps{
                withSonarQubeEnv('sonar-server'){ // Use the SonarQube server configured in Jenkins
                    sh """
                        sonar-scanner \
                        -Dsonar.projectKey=myprojectn \
                        -Dsonar.projectName=myprojectk \
                        -Dsonar.sources=src \
                        -Dsonar.java.binaries=target/classes \
                        -Dsonar.host.url=http://13.233.238.150:9000
                    """
                }
            }
        }
    }
}
