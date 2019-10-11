node {
    stage('Git upload'){
      // def mvnTool = tool 'Apache Maven 3.6.2'
        
      //  sh "${mvnTool}/bin/mvn/ clean install"
        sh "echo hello world"
    }
    stage('shell'){
        sh '''
        echo "chal na yar"
        '''
    }
    stage('post build'){
        echo "email to the user about the build status"
    }
    
}
