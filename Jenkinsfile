pipeline{
  agent{
    label 'master'
  }
  
  stages{
    stage('PRINT'){
      steps{
        echo "In PRINT stage and job name is $JOB_NAME"
      }
    }

    stage('WRITE'){
      steps{
        echo "In WRITE stage and job name is $JOB_NAME"
        sh 'echo "$BUILD_NUMBER" >> build_number'
      }
    }

    stage('READ'){
      steps{
        sh 'cat build_number'
      }
    }
  }
  post {
        success {
            archiveArtifacts artifacts: 'build_number', fingerprint: true
        }
    }
}
