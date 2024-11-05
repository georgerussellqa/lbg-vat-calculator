pipeline {
  agent any

  stages {
    stage('SonarQube Analysis') {
      environment {
        scannerHome = tool 'sonarqube'
      }
        steps {
            withSonarQubeEnv('sonarqube-server-1') {        
              sh "${scannerHome}/bin/sonar-scanner"
            }   
            timeout(time: 10, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: true
            }
        }
    }
  }
}
