pipeline {
    environment {
      registryCredential = ''
      registryUri = 'http://kube1.local:5000/'
    }
    
    agent { dockerfile {
        filename 'Dockerfile'
//        additionalBuildArgs  "--build-arg CACHEBUST=${env.BUILD_TAG}"
        additionalBuildArgs  "--no-cache"
            } 
          }
    stages {
        stage('Test Scripts') {
            steps{
                script {
                    sh  'checkov --version'
                    }
             }
         }
     }

  post {
        always {
            echo 'One way or another, I have finished'
//            deleteDir() /* clean up our workspace */
        }
        success {
            echo 'I succeeded!'
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things were different before...'
        }
  }
}
