pipeline {
    agent { label 'nop' }
    triggers { pollSCM('* * * * *') }
    stages {
        stage('git clone stage') {
            steps {
                git credentialsId: '12345',
                    branch: 'master',
                    url: 'https://github.com/shaifalikhan5/nopCommerce-july23.git'
            }
        }

           stage('buildstage') {
            steps {
            sh 'dotnet restore src/NopCommerce.sln'
            sh 'dotnet build -c Release src/NopCommerce.sln'
            sh 'dotnet publish -c Release src/Presentation/Nop.Web/Nop.Web.csproj -o publish'
            sh 'mkdir publish/logs publish/bin && zip -r NopCommerce.zip publish'
            
            }
           }
             stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: "${publish}/**", allowEmptyArchive: true
            }

    }
}





