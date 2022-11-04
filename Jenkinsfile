pipeline {
   agent any
   environment {
    DOCKERHUB_CREDENTIALS=credentials('dockerhub_credentials')
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
                    docker images
                    make base
                    cd nf_udr
                    docker build -t gradproj/udr .
                    docker push gradproj/udr
                    cd ..
                """)
                }
        }
    }
}