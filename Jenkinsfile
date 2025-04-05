pipeline{
      agent any

      stages{
         stage('zip file'){
                  steps{
                           
                           sh 'rm -rf *.zip || echo ""'
                           sh 'zip -r ansible-${BUILD_ID}.zip * --exclude Jenkinsfile'
                  }
         }
         stage('publish to ansible server'){
                  steps{
                           sshPublisher(publishers: [sshPublisherDesc(configName: 'ansible-server', \
                           transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'unzip ansible-${BUILD_ID}.zip; rm -rf ansible-${BUILD_ID}.zip', execTimeout: 120000, flatten: false, \
                           makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '.', \
                           remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'ansible-${BUILD_ID}.zip')], usePromotionTimestamp: false, \
                           useWorkspaceInPromotion: false, verbose: false)])
                  }
         }


      }


}