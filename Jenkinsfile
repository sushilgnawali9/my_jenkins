node('maven') {
    stage('Git upload'){
      def mvnTool = tool 'Apache Maven 3.6.2'
        
      sh "${mvnTool}/bin/mvn clean install"
        junit allowEmptyResults: true, testResults: 'target/surefire-reports.*.xml'
        
    }
    stage('shell'){
        sh '''
        echo "chal na yar"
        '''
    }
    stage('post build'){
        sh "echo sakkigo ni"
    }
    
}
