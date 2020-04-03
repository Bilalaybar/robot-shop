pipeline {
    agent any
    stages {
      stage('Docker Push') {
        steps {
          sh "echo pushing"
        }
      }
      stage('Deploy') {
        steps {
            sh "helm upgrade --install robot-shop K8s/helm --namespace=robot-shop"
            }
        }
      }
}
