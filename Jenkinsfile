pipeline {
    agent any
    stages {
      stage('Docker Push') {
        steps {
          sh "echo pushing"
        }
      }
      stage('scan'){
        steps {
          twistlockScan ca: '', cert: '', compliancePolicy: 'medium', containerized: true, dockerAddress: 'unix:///var/run/docker.sock', gracePeriodDays: 1, ignoreImageBuildTime: true, image: 'robotshop/rs-cart:latest', key: '', logLevel: 'true', policy: 'medium', requirePackageUpdate: false, timeout: 10
        }
      }
      stage('Deploy') {
        steps {
            sh "helm upgrade --install robot-shop K8s/helm --namespace=robot-shop"
            }
        }
      }
}
