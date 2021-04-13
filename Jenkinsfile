pipeline {
  stages {

    stage('Build') {
      environment {
        DOCKERHUB_CREDS = credentials('dockerhub')
      }
      steps {       
          // Build new image
          sh "until docker ps; do sleep 3; done && docker build -t shivaprasadreddy1/loan-price-demo-app:${env.GIT_COMMIT} ."
          // Publish new image
          sh "docker login --username $DOCKERHUB_CREDS_USR --password $DOCKERHUB_CREDS_PSW && docker push shivaprasadreddy1/loan-price-demo-app:${env.GIT_COMMIT}"
      }
    }
  }
}
