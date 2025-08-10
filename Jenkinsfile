pipeline {
  agent any
  
  options {
    skipDefaultCheckout()
  }
  
  environment {
    PROJECT_NAME = "jenkins-CI-best-practice"
  }

  parameters {
    string defaultValue: 'main', description: 'Branch to checkout', name: 'branch_name', trim: true
    booleanParam description: 'Enable debug mode', name: 'debug_mode'
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
