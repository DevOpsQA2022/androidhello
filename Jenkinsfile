pipeline {
    agent any
    tools{
      docker 'Docker'
    }
    stages {
        stage ('Build') {
            
            steps { 
                sh ' docker build. -f manjula28112022/devopsqa '                            
//                sh 'gradle build' 
                echo "successfully build"
                
            }        
        }      
         stage ('push') {
             steps {
                withDockerRegistry(credentialsId: '	ec4e4d32-bd3f-4eba-a3bf-ea1f00b6d1fb', url: 'https://hub.docker.com/repository/docker/manjula28112022/devopsqa'){
                     sh ' docker push manjula28112022/devopsqa '
                }
             }
               
        }
    }
}
