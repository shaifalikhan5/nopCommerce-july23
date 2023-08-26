pipeline {
    agent { label 'nop' }
    triggers { pollSCM('* * * * *') }
    stages {
        stage('git clone stage') {
            steps {
                git credentialsId: '12345',
                    branch: 'master'
                    url: 'https://github.com/shaifalikhan5/nopCommerce-july23.git'
            }
        }
    }




}