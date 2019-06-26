node {
   stage('Preparation') { 
       // checkout from our repository
      git 'https://github.com/AbrahamCalderon/fleetman-position-tracker'
   }
   stage('Build') {
      sh 'mvn package'
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archiveArtifacts 'target/*.jar'
   }
   stage('Deploy') {
      ansiblePlaybook credentialsId: 'SSH-CRED', installation: 'ansible-installation', playbook: 'deploy.yaml'
   }
}
