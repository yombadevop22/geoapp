pipeline {

    agent any

    environment {
      BRANCH_NAME = 'main'
      GIT_URL = 'https://github.com/yombadevop22/geoapp.git'
      GITHUB_CREDENTIALS = 'github-credentials'
    }

    stages{
        stage('git checkout') {
            steps{
              git branch: "${BRANCH_NAME}", credentialsId: "${GITHUB_CREDENTIALS}", \
              url: "${GIT_URL}"
            }
    }
}