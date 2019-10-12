node('maven') {
    stage('Git upload'){
      def mvnTool = tool 'Apache Maven 3.6.2'
        
      sh "${mvnTool}/bin/mvn clean package"
        junit allowEmptyResults: true, testResults: 'target/surefire-reports.*.xml'
        
    }
    stage('Artifacts'){
        archiveArtifacts '**/target/*.war'
    }
    stage('deployment')
    {
        sshagent(['ec2-user'])
        {
            sh "ssh -o StrictHostKeyChecking=no ec2-user@34.205.159.165 /home/ec2-user/tomcat9/bin/startup.sh"
        }
    }
    stage('post build'){
        sh "echo sakkigo ni"
    }
    
}
