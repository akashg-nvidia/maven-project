pipeline {
    agent any
    
    triggers {
         pollSCM('* * * * *') // Polling Source Control
     }
         environment{
       mvnHome = tool 'localMaven'
        }
stages{
        stage('Build'){
            steps {
                sh 'mvnHome clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}
