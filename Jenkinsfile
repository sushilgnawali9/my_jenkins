node('maven') {
    stage('Git upload'){
      def mvnTool = tool 'Apache Maven 3.6.2'
        
      sh "${mvnTool}/bin/mvn clean package"
        junit allowEmptyResults: true, testResults: 'target/surefire-reports.*.xml'
        
    }
    stage('Artifacts'){
        archiveArtifacts '**/target/*.war'
    }
    stage ('docker build')
    {
       sh  "docker version"
       sh " docker build -t sushil321/archiveartifacts ."
       sh "docker run -d sushil321/archiveartifacts"
       sh "docker push sushil321/archiveartifacts"
    }
    stage('deployment')
    {
        sshagent(['ec2-user'])
        {
            sh "ssh -o StrictHostKeyChecking=no ec2-user@54.80.200.161 /home/ec2-user/tomcat9/bin/startup.sh"
            //sh "scp -o StrictHostKeyChecking=no /home/ec2-user/workspace/pipe-line-project/target/addressbook.war ec2-user@3.88.86.159:/home/ec2-user/tomcat9/webapps"
        }
    }
    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-key-shared', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                sh "aws s3 cp target/addressbook.war s3://sushildarling/"
}
    stage('post build'){
        sh "echo sakkigo ni"
    }
    
}
