pipeline{
    agent any
    tools{
	maven "maven3.9.9"
	}
    stages{
        stage("Checkout from GitHub"){
            steps{
                git branch: 'main', url: 'https://github.com/vpolachi/jenkins-java-cicd.git'
            }
        }
        stage("maven tests"){
            steps{
                sh 'mvn test'
            }
        }
        stage("maven build"){
            steps{
                sh 'mvn clean package'
            }
        }
	stage("OWASP Dependency-Check"){
	    steps{	
	    	sh "/opt/dependency-check/bin/dependency-check.sh --scan /var/lib/jenkins/workspace/petclinic-cicd/target --format ALL"
            }
        }
    }

}

