pipeline{
    //Directives
    agent any
    tools {
        maven 'Maven'
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

        // Stage3 : Publish the source code to Ansibleserver
        stage ('Storing Artificat'){
            steps {
              
            sh 'sshPublisher(publishers: [sshPublisherDesc(configName: 'ansibleserver', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: ''//opt/playbooks', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'webapp/target/*.war'')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])'
            
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