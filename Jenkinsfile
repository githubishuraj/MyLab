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

        // Stage3 : Publish the source code to Sonarqube
        stage ('Publish to Nexus'){
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'irbDevOpsLab', classifier: '', file: 'target/irbDevOpsLab-0.0.8-SNAPSHOT.war', type: 'war']], credentialsId: '', groupId: 'com.irbdevopslab', nexusUrl: '172.20.10.104:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'irbDevopsLab-Snapshot', version: '0.0.8-SNAPSHOT'
                }

            }
        stage ('deploy'){
            echo 'deploying....'
        
        
        }

        
        
    }

}
