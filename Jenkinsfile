pipeline {
  agent { label 'jenkins-Agent' }
  
  tools {
    jdk 'Java17'
    maven 'Maven3'
  }

  stages {
    stage("Cleanup Workspace") {
      steps {
        cleanWS()
      }
    }

    stage("Checkout from SCM") {
      steps {
        git branch: 'main', credentialsId: 'github', url: 'https://github.com/BabaGee01/register-app'
      }
    }

    stage("Build Application") {
      steps {
        sh "mvn clean package"
      }
    }

    stage("Test Application") {
      steps {
        sh "mvn test"
      }
    }
  }

  post {
    always {
      echo "Build process completed."
    }
  }
}
