
pipeline {
    agent any

    stages {
        stage('upload') {
           steps {
              script { 
                 def server = Artifactory.newServer url: 'jfrog-1', credentialsId: 'jfrog'
                 def uploadSpec = """{
                    "files": [{
                       "pattern": "*.md",
                       "target": "generic-local/"
                    }]
                 }"""

                 server.upload(uploadSpec) 
               }
            }
        }
    } 
}
