pipeline {
    agent any
    stages {
        stage ("Deploy PHP application") {
           steps {
               sshPublisher(publishers: [sshPublisherDesc(configName: 'Apache2-php8.0', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/var/www/html/', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '**/*.php')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
           } 
        }
    }
}
