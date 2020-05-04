def gitSourceUrl=env.GIT_SOURCE_URL
def gitSourceRef=env.GIT_SOURCE_REF
def project=env.PROJECT_NAME
def projectVersion=""	

pipeline {
  agent {
    label 'maven'
  }
  stages {
    stage('Initialize') {
      steps {
        echo "gitSourceUrl: ${gitSourceUrl}"
        echo "gitSourceRef: ${gitSourceRef}"
        echo "Nexus user: ${env.MAVEN_SERVER_USERNAME}"
      }
    }
    stage('Checkout') {
      steps {
        echo "Checkout source."
        git url: "${gitSourceUrl}", branch: "${gitSourceRef}"
      }
    }
    stage('Build and Deploy POM') {
      steps {
        echo "Build the POM."
        sh "mvn deploy"
      }
    }
  }
}