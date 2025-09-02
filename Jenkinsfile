// Demostrate how to declare build parameters in Jenkinsfile

pipeline {
  agent any
  
  options {
    skipDefaultCheckout()
  }

  environment {
    PROJ_NAME = 'TEST_BUILD_PARAMETERS'
  }

  parameters {
    string defaultValue: '', description: 'Branch to be checked out', name: 'branch_name', trim: true
    choice choices: ['DEV', 'SIT', 'UAT', 'PROD'], name: 'test_env'
    file description: 'Configuration file', name: 'config_file'
    password defaultValue: '', description: 'User password', name: 'user_pass'
    run description: 'Dependent build of specified job', filter: 'ALL', name: 'dependsOn_build', projectName: "${JOB_NAME}"
    credentials credentialType: 'com.cloudbees.plugins.credentials.impl.UsernamePasswordCredentialsImpl', defaultValue: '', description: 'Required credential to perform actions', name: 'user_credential', required: true
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
      when {
        expression {
          return params.branch_name.length() > 0
        }
      }
      
      steps {
        echo "testing...."
        echo "params.branch_name=${params.branch_name}"
         echo "params.test_env=${params.test_env}"
         echo "params.user_pass=${params.user_pass}"
        
         echo "params.dependsOn_build=${params.dependsOn_build}"
         echo "dependsOn_build=${dependsOn_build}"
         echo "dependsOn_build_JOBNAME=${dependsOn_build_JOBNAME}"
         echo "dependsOn_build_NUMBER=${dependsOn_build_NUMBER}"
         echo "dependsOn_build_NAME=${dependsOn_build_NAME}"
         echo "dependsOn_build_RESULT=${dependsOn_build_RESULT}"
        
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
