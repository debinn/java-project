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
        sh 'echo $BUILD_NUMBER >> build_number'
      }
    }

    stage('READ'){
      steps{
        sh 'cat build_number'
      }
    }
    
    stage('DEPLOY'){
      steps{
        sh 'ant -f build.xml -v' 
      }
    }
    
    stage('RESULT'){
      steps{
        sh 'java jar dist/rectangle.jar 4 5'
      }
    }
  }
  post {
        success {
            archiveArtifacts artifacts: 'build_number', fingerprint: true
        }
    }
}
