pipeline{

  agent any

  environment {
      DOCKERHUB_CREDENTIALS=credentials('dockerhub-teptrol')
    }

  stages {

           stage('Login') {

            steps {
                    sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                  }
          }
          stage('Build') {

            steps {
                    sh './mvnw clean install -P buildDocker '
                  }
          }


    }

  post {
      always {
            sh 'docker logout'
          }
    }

}

