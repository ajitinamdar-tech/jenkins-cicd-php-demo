pipeline {
    agent any 
    stages {
//         stage('SCM Checkout') {
//             steps {
//                 git branch: 'main', url: 'https://github.com/Bala0911/jenkins-cicd-php-demo.git'
//             }
//         }
        stage('Deploy') {
            steps {
                sh 'ssh ubuntu@15.207.110.140 "sudo rm -i /var/www/html/*"'
                sshPublisher(publishers: [sshPublisherDesc(configName: 'php-server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/var/www/html/', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '**/*')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
                sh 'ssh ubuntu@15.207.110.140 "sudo systemctl restart apache2"'
            }
        }
                    
    }
}
