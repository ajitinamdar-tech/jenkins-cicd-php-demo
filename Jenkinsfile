
pipeline{
    agent any
    environment{
        staging_server="172.31.7.52"
    }
    stages{
        stage('SCM Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Bala0911/jenkins-cicd-php-demo.git'
            }
        }
        stage('sonarqube analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    script {
                        def scannerHome = tool 'SonarQube Scanner'
                        withEnv(["PATH+SONARSCANNER=${scannerHome}/bin"]) {
                            sh 'sonar-scanner \
                                -Dsonar.projectKey=sample-php-app \
                                -Dsonar.sources=${WORKSPACE}'
                        }
                    }
                }
            }
        }
        stage('Deploy master to server'){
            when {
                branch 'main'
            }
            input {
                    message "Approve deployment?"
                }
            steps{
                sh 'rsync -avzh * --exclude=.git --exclude=*.PNG --exclude=.scannerwork --delete . ubuntu@${staging_server}:/var/www/html/'
                // sh 'scp -r -o StrictHostKeyChecking=no books/ bookstore/ test/ root@${staging_server}:/var/www/html/'
            }
        }
        stage('Deploy staging to server '){
            when {
                branch 'test'
            }
            input {
                    message "Approve deployment?"
                }
            steps{
                sh 'rsync -avzh * --exclude=.git --exclude=*.PNG --exclude=.scannerwork --delete . ubuntu@${staging_server}:/var/www/html/'
                // sh 'scp -r -o StrictHostKeyChecking=no books/ bookstore/ test/ root@${staging_server}:/var/www/html/'
            }
        }
    }
}
