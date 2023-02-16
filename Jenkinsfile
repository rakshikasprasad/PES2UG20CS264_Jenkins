pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'g++ main/test.cpp -o output'
        build 'PES2UG20CS264-1'
        echo 'Build Successful'
      }
    }
    stage('Test') {
      steps {
        sh './output'
        echo 'Testing Successful'
      }
    }
    stage('Deploy') {
      when {
        expression {
          currentBuild.result == null || currentBuild.result == 'SUCCESS' 
        }
      }
      steps {
        echo 'Deployment Successful'
      }
    }
  }
  post {
    always {
       echo 'Pipeline completed'
    }
    failure {
      echo 'Pipeline failed'
    }
  }
}
