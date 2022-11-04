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
        stage('Login') {

            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
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