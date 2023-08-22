pipeline {
   agent { label 'nop' }
   stages{
    stage( 'git clone stage' ) {
       steps { git url: 'https://github.com/shaifalikhan5/nopCommerce-july23.git',
                   branch: 'master'
            }
    }
    stage('build stage') {
        steps {
               sh script: 'dotnet restore src/NopCommerce.sln'
               sh script: 'dotnet build -c Release src/NopCommerce.sln'
               sh 'dotnet publish -c Release src/Presentation/Nop.Web/Nop.Web.csproj -o publish'
               sh 'sudo apt install zip -y'
               sh 'mkdir publish/bin publish/logs &&  zip -r NopCommerce.zip publish/bin' 
        }
        

    }
    stage('artifact') {
        steps {
            archiveArtifacts artifacts: '**/NopCommerce.zip'
        }
    }

   }

}