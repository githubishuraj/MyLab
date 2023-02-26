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
                nexusArtifactUploader(
        nexusVersion: 'nexus3',
        protocol: 'http',
        nexusUrl: 'my.nexus.address',
        groupId: 'com.vinaysdevopslab',
        version: '0.0.8',
        repository: 'irbDevopsLab-SNAPSHOT',
        credentialsId: 'fb698bd7-e3e5-44b5-ac4b-ffe5063c5651',
        artifacts: [
            [artifactId: 'VinayDevOpsLab',
             classifier: '',
             file: 'VinayDevOpsLab-0.0.8.war',
             type: 'war']
        ]
     )
                }

            }
        stage ('deploy'){
            steps {
            echo 'deploying....'
            }
        
        
        }

        
        
    }

}
