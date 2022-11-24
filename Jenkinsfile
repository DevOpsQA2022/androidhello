pipeline {
    agent any
//     tools{
//       gradle 'gradle'
//     }
    stages {
        stage('Build') {
             agent {
                docker {
                    image 'gradle:7.3-jdk17'
                    reuseNode true
                }
             }
            steps {  
                sh ' gradle --version'
               
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
