pipeline {
    agent { label 'nop' }
    triggers { pollSCM('* * * * *') }
    stages {
        stage('git clone stage') {
            steps {
                git credentialsId: '12345',
                    branch: 'develop',
                    url: 'https://github.com/shaifalikhan5/nopCommerce-july23.git'
            }
        }

           stage('buildstage') {
            steps {
            sh 'dotnet restore src/NopCommerce.sln'
            sh 'dotnet build -c Release src/NopCommerce.sln'
            sh 'dotnet build -c Release src/Presentation/Nop.Web.csproj -o publish'
            sh 'mkdir publish/bin publish/logs' 
            }
            

    }
     stage('results') {
            steps{
                archiveArtifacts artifacts: '**/*.dll'
            }
}
}
}





