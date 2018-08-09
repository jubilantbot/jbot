
pipeline { 
    agent any  
    stages { 
        stage('Build') { 
            steps { 
               echo 'This is a minimal pipeline.' 
               script{
                    // Obtain an Artifactory server instance, defined in Jenkins --> Manage:
                    def server = Artifactory.server jfrog-1

                    // Read the download and upload specs:
                    // def downloadSpec = readFile 'jenkins-examples/pipeline-examples/resources/props-download.json'
                    def uploadSpec = readFile 'artifactory.json'

                    // Download files from Artifactory:
                    // def buildInfo1 = server.download spec: downloadSpec
                    // Upload files to Artifactory:
                    def buildInfo2 = server.upload spec: uploadSpec

                    // Merge the local download and upload build-info instances:
                    buildInfo1.append buildInfo2

                    // Publish the merged build-info to Artifactory
                    server.publishBuildInfo buildInfo1
                }
            
            }
        }
    }
}
