pipeline {

    agent any
    tools {
        maven 'M2_HOME'
    }

    environment {
      BRANCH_NAME = 'main'
      GIT_URL = 'https://github.com/yombadevop22/geoapp.git'
      GITHUB_CREDENTIALS = 'github-credentials'
      SONAQUBE_CRED = 'Sonar-Cred'
      SONAQUBE_INSTALLATION = 'Sonar-server'
      APP_NAME = 'geoapp'
    }

    stages{
        stage('git checkout') {
            steps{
              git branch: "${BRANCH_NAME}", credentialsId: "${GITHUB_CREDENTIALS}", \
              url: "${GIT_URL}"
            }
    }
        stage('unit test') {
            steps {
                sh 'mvn clean'
                sh 'mvn test'
                sh 'mvn compile'
            }
        }
        stage('Sonarqube Scan'){
            steps{
                WithSonarQubeEnv(credentialsID: "${SONAQUBE_CRED}", installationName: "${SONAQUBE_INSTALLATION}" ) {
              sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=${APP_NAME} -Dsonar.projectKey=${APP_NAME} -Dsonnar.java.binaries=. '''
                }
            }
        }
        
}

}