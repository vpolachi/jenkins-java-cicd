pipeline{
    agent any
        tools{
            maven 'maven3.9.9'
            sonarRunner 'sonar-scanner'
        }
    stages{
        stage("Checkout"){
            steps{
                checkout scm
            }
        }
         stage("maven compile"){
            steps{
                sh 'mvn compile'
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
                        sonar-scanner \
                            -Dsonar.projectKey=myprojectn \
                            -Dsonar.projectName=myprojectnk \
                            -Dsonar.sources=src \
                            -Dsonar.java.binaries=target/classes \
                            -Dsonar.host.url=http://13.233.238.150:9000 \
                            -Dsonar.login=squ_9570f50ccb5ec07e2cdf1add3feaaeb12eb445bb
                    """
                }
            }
        }
    }
}
