pipeline {
    agent any
    tools{
      gradle 'gradle'
    }
    stages {
        stage('Build') {              
            steps {                
               sh 'gradle build --warning-mode=all' 
                echo "successfully build"
                
            }
              post{
                 success{
                     echo "Archiving the Artifacts"
                     archiveArtifacts artifacts: '**/debug/*.apk'                             
                 }
            }            
        }            
    }
}
