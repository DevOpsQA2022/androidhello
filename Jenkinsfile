pipeline {
    agent any
    tools{
      gradle 'gradle'
    }
    stages {
        stage('Build') {
            
            steps {  
                            
               bat 'gradle build'
                echo "successfully build"
                
            }
              post{
                 success{
                     echo "Archiving the Artifacts"
                     archiveArtifacts artifacts: '**/debug/*.apk'                             
                 }
            }    
            script {
              timeout(time: 10, unit: 'MINUTES') {
                input(id: "Deploy Gate", message: "deploy?", ok: 'Deploy')
              }
            }

        }      
            stage('Test'){
                post{
                    success{
                        emailext body: '', recipientProviders: [developers()], subject: 'build', to: 'manjula.r@ciglobalsolutions.com'
                    }
                }
                steps {
                    echo "successfully"
                }
            }
    }
}
