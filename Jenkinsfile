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
          stage("SonarQube Analysis"){
            steps{
                withSonarQubeEnv('Sonar-server'){ //Use the SonarQube server configured in Jenkins
                    sh """
                        docker run --rm \
                        -v "$WORKSPACE:/usr/src" \
                        sonarsource/sonar-scanner-cli:latest \
                        sonar-scanner \
                        -Dsonar.projectKey=myprojectn \
                        -Dsonar.projectName=myprojectnk \
                        -Dsonar.sources=src \
                        -Dsonar.java.binaries=target/classes \
                        -Dsonar.host.url=http://13.233.238.150:9000
                    """
                }
            }
        }
    }
}
