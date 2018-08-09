
pipeline { 
    agent any  
    stages { 
        stage('Build') { 
            steps { 
               echo 'This is a minimal pipeline.' 
               script{
                    // Obtain an Artifactory server instance, defined in Jenkins --> Manage:
                    def server = Artifactory.newServer url: 'jfrog-1', credentialsId: 'jfrog'
                    def uploadSpec = readFile 'artifactory.json'
                    server.upload(uploadSpec)
                }
            
            }
        }
    }
}
