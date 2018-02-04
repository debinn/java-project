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
    
    stage('UNIT TESTS'){
      steps{
        sh 'ant -f test.xml -v' 
        junit 'reports/result.xml'
      }
    }
    
    stage('BUILD'){
      steps{
        sh 'ant -f build.xml -v' 
      }
    }
    
     stage('DEPLOY'){
      steps{
        sh 'ls -la dist/'
        sh 'BUILD_NUMBER=env.BUILD_NUMBER'
        sh 'cp dist/rectangle_${env.BUILD_NUMBER}.jar /var/www/html/rectangle/all/' 
      }
    }
  }
  post {
        success {
            archiveArtifacts artifacts: 'build_number', fingerprint: true
        }
    }
}
