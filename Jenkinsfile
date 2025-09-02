pipeline {
  agent any
  
  options {
    skipDefaultCheckout()
  }
  
  environment {
    PROJECT_NAME = "jenkins-CI-best-practice"
  }

  parameters {
    string defaultValue: 'test-build-parameters', description: 'Branch to be checked out', name: 'branch_name', trim: true
    choice choices: ['DEV', 'SIT', 'UAT', 'PROD'], name: 'test_env'
    file description: 'Configuration file', name: 'config_file'
    password defaultValue: '', description: 'User password', name: 'user_pass'
    run description: 'Dependent build of specified job', filter: 'ALL', name: 'dependsOn_build_no', projectName: "${JOB_NAME}"
    credentials credentialType: 'com.cloudbees.plugins.credentials.impl.UsernamePasswordCredentialsImpl', defaultValue: 'Required credential to perform actions', description: '', name: 'user_credential', required: true
    booleanParam defaultValue: true, description: 'Detect incedent toggle', name: 'detect_incident'
    booleanParam defaultValue: false, description: 'Debug mode toggle', name: 'debug_mode'
    text defaultValue: '', description: 'Additional gradle opts', name: 'extra_gradle_opts'
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
        echo "params.branch_name=${params.branch_name}"
         echo "params.test_env=${params.test_env}"
         echo "params.user_pass=${params.user_pass}"
         echo "params.dependsOn_build_no=${params.dependsOn_build_no}"
         echo "params.user_credential=${params.user_credential}"
         echo "params.detect_incident=${params.detect_incident}"
         echo "params.debug_mode=${params.debug_mode}"
         echo "params.extra_gradle_opts=${params.extra_gradle_opts}"
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
