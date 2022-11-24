pipeline {
    agent { docker { image 'gradle:7.3' } }
    
//     tools{
//       gradle 'gradle'
//     }
    stages {
        stage('Build') {              
            steps {  
                sh 'gradle --version'
                sh 'gradle install'
               sh 'gradle clean build' 
                echo "successfully build"
                
            }
              post{
                 success{
                     echo "Archiving the Artifacts"
                     archiveArtifacts artifacts: '**/debug/*.apk'                             
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
