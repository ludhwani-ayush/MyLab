pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }
    environment{
       ArtifactId = readMavenPom().getArtifactId()
       Version = readMavenPom().getVersion()
       Name = readMavenPom().getName()
       GroupId = readMavenPom().getGroupId()
    }
    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }

        // Stage3 : Publish the source code to S3
        stage ('Storing Artificat'){
            steps {
                s3Upload consoleLogLevel: 'INFO', 
                dontSetBuildResultOnFailure: false, 
                dontWaitForConcurrentBuildCompletion: false, 
                entries: [[bucket: 'myartifacts-bucket-1995', 
                excludedFile: '/webapp/target', flatten: false, 
                gzipFiles: false, keepForever: 
                false, managedArtifacts: false, 
                noUploadOnFailure: true, 
                selectedRegion: 'us-east-1', 
                showDirectlyInBrowser: false, 
                sourceFile: '**/webapp/target/*.war', 
                storageClass: 'STANDARD', 
                uploadFromSlave: false, 
                useServerSideEncryption: false]], 
                pluginFailureResultConstraint: 'FAILURE', 
                profileName: 's3artifactdemo', 
                
            }
        }



        // Stage 4 : Deploying the build artifact to Apache Tomcat
        stage ('Deploy to Tomcat'){
            steps {
                echo "Deploying ...."
            
            }
        }

    




    }

}