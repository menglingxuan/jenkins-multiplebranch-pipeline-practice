pipeline {
  agent any
  
  stages {
    environment {
      PROJECT_NAME = "jenkins-CI-best-practice"
    }
    
    stage('Build') {
      echo "building...."
    }
    
    stage('Test') {
      echo "testing...."
    }
    
    stage('Deploy') {
      echo "deploying...."
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
}
