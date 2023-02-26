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

        
        stage ('Publish to Nexus'){
            steps {
                nexusArtifactUploader(
        nexusVersion: 'nexus3',
        protocol: 'http',
        nexusUrl: '172.20.10.104:8081',
        groupId: 'com.vinaysdevopslab',
        version: '0.0.9',
        repository: 'irb',
        credentialsId: 'bf9a5b7c-fff9-49b8-8354-6f0931ce7e01',
        artifacts: [
            [artifactId: 'VinayDevOpsLab',
             classifier: '',
             file: 'target/VinayDevOpsLab-0.0.9.war',
             type: 'war']
        ]
     )
                }

            }
        stage('print environment variables')
        {
           steps {
               echo "ArtifactId id '${ArtifactId}'"
               echo "Version is '${Version}'"
               echo "Name is '${Name}'"
               echo "GroupId is ${GroupId}"
    }
}
        stage ('deploy'){
            steps {
            echo 'deploying....'
            }
        
        
        }

        
        
    }

}
