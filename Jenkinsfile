node {
    stage('Git upload'){
       def mvnhome = tool name: 'maven-3.6.2', type: 'maven' 
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
