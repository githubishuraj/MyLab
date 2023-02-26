pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
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

        
        stage ('Publish to Nexus'){
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'irbDevOpsLab', classifier: '', file: 'target/irbDevOpsLab-com.irbdevopslab.war', type: 'war']], credentialsId: '', groupId: 'com.irbdevopslab', nexusUrl: '13.58.74.188:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'irbDevopsLab-Snapshot', version: '0.0.8-SNAPSHOT'
                }

            }
        stage ('deploy'){
            steps {
            echo 'deploying....'
            }
        
        
        }

        
        
    }

}
