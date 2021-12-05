pipeline {
  agent any
  
  options {
    skipDefaultCheckout()
  }
  
  environment {
    PROJECT_NAME = "jenkins-CI-best-practice"
  }
  
  stages {
    stage('Build') {
      steps {
        echo "building...."
      }
    }
    
    stage('Test') {
      steps {
        echo "testing...."
      }
    }
    
    stage('Deploy') {
      steps {
        echo "deploying...."
      }
    }
  }
  
  post {
    always {
      echo "completed!"
    }
      
    success {
      echo "success!"
    }
      
    failure {
      echo "failed!"
    }
  }
}
