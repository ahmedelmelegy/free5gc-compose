pipeline {
   agent any
//    environment {
//     DOCKERHUB_CREDENTIALS = credentials('docker_hub')
//    }

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }

        stage('docker build') {
            steps {
                sh(script: """
                    docker images
                """)
                }
        }
    }
}
