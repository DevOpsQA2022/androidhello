pipeline {
    agent any
    tools{
      gradle 'gradle'
    }
    stages {
        stage('Build') {              
            steps {                
               sh 'gradle build' 
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
