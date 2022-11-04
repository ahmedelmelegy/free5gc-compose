pipeline {
   agent any
   environment {
    DOCKERHUB_CREDENTIALS = credentials('docker_hub')
   }

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }

        stage('docker build') {
            steps {
                sh(script: """
                    sudo make base
                    cd nf_udr
                    sudo docker images
                """)
                }
        }
    }
}
