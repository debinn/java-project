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
        sh 'echo "$BUILD_NUMBER" >> $WORKSPACE/build_number.txt'
      }
    }

    stage('READ'){
      steps{
        echo "cat $WORKSPACE/build_number.txt"
      }
    }
  }
}
