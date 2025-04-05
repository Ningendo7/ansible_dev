pipeline{
      agent any

      stages{
         stage('zip file'){
                  steps{
                           sh 'zip ansible-${BUILD_ID}.zip * --exclude Jenkinsfile'
                           sh 'ls -l'
                  }


         }


      }


}