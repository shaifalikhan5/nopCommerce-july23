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
               sh script 'dotnet restore src/NopCommerce.sln'
               sh script 'dotnet build -c Release src/NopCommerce.sln'
        }

    }

   }

}