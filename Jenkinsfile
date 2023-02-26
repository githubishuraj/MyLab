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
        nexusUrl: '172.20.10.104:8081',
        groupId: 'com.vinaysdevopslab',
        version: '0.0.8',
        repository: 'irbDevopsLab-SNAPSHOT',
        credentialsId: 'bf9a5b7c-fff9-49b8-8354-6f0931ce7e01',
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
