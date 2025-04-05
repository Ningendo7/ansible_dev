pipeline{
      agent any

      stages{
         stage('zip file'){
                  steps{
                           sh 'zip ansible-${BUILD_ID}.zip ansible-dev --exclude Jenkinsfile'
                  }
         }
         stage('publish to ansible server'){
                  steps{
                           sshPublisher(publishers: [sshPublisherDesc(configName: 'ansible-server', \
                           transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, \
                           makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '.', \
                           remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'ansible-${BUILD_ID}.zip')], usePromotionTimestamp: false, \
                           useWorkspaceInPromotion: false, verbose: false)])
                  }
         }


      }


}