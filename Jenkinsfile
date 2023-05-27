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
                sh 'scp -o StrictHostKeyChecking=no **/*.php ubuntu@172.31.9.1:/var/www/html/'
                // sh 'ssh -o StrictHostKeyChecking=no ubuntu@172.31.9.1 "sudo rm -i /var/www/html/*"'
                // sshPublisher(publishers: [sshPublisherDesc(configName: 'php-server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/var/www/html/', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '**/*.php')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
                // sh 'ssh -o StrictHostKeyChecking=no ubuntu@172.31.9.1 "sudo systemctl restart apache2"'
            }
        }
                    
    }
}
        stage('Deploy') {
            steps {
                sh 'scp -r -o StrictHostKeyChecking=no ${WORKSPACE}/* root@<ip>:/var/www/html/<jpb-name>'
            }
        }