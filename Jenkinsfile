pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }
//         environment{
//            ART = readMavenPom().getArtifactId()
//            VER = readMavenPom().getVersion()
//            NAME = readMavenPom().getName()
//            GID = readMavenPom().getGroupId()
// }

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
        nexusUrl: '3.17.9.49:8081',
        groupId: 'com.vinaysdevopslab',
        version: '0.0.8',
        repository: 'irb',
        credentialsId: 'bf9a5b7c-fff9-49b8-8354-6f0931ce7e01',
        artifacts: [
            [artifactId: 'VinayDevOpsLab',
             classifier: '',
             file: 'target/VinayDevOpsLab-0.0.8.war',
             type: 'war']
        ]
     )
                }

            }
//         stage('print environment variables')
//         {
//            steps {
//                echo "ArtifactId id '${ART}'"
//                echo "Version is '${VER}'"
//                echo "Name is '${NAME}'"
//                echo "GroupId is ${GID}"
//     }
// }
        stage ('deploy'){
            steps {
            echo 'deploying....'
                sshPublisher(publishers:
 [sshPublisherDesc(configName: 'Ansible_Controller',
  transfers:
   [sshTransfer(cleanRemote: false, excludes: '',
    execCommand: 'ansible-playbook /opt/playbooks/dandi.yml -i /opt/playbooks/hosts', execTimeout: 120000, 
    flatten: false, makeEmptyDirs: false,
     noDefaultExcludes: false,
      patternSeparator: '[, ]+', 
      remoteDirectory: '', remoteDirectorySDF: false, 
      removePrefix: '', sourceFiles: '')],
       usePromotionTimestamp: false, useWorkspaceInPromotion: false, 
       verbose: false)])
            }
        
        
        }

       stage ('deploy to docker'){
            steps {
            echo 'deploying....'
                sshPublisher(publishers:
 [sshPublisherDesc(configName: 'Ansible_Controller',
  transfers:
   [sshTransfer(cleanRemote: false, excludes: '',
    execCommand: 'ansible-playbook /opt/playbooks/danddocker.yml -i /opt/playbooks/hosts', execTimeout: 120000, 
    flatten: false, makeEmptyDirs: false,
     noDefaultExcludes: false,
      patternSeparator: '[, ]+', 
      remoteDirectory: '', remoteDirectorySDF: false, 
      removePrefix: '', sourceFiles: '')],
       usePromotionTimestamp: false, useWorkspaceInPromotion: false, 
       verbose: false)])
            }
        
        
        } 
        
    }

}
