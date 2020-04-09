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
          twistlockScan ca: '', cert: '', compliancePolicy: 'high', containerized: true, dockerAddress: 'unix:///var/run/docker.sock', gracePeriodDays: 1, ignoreImageBuildTime: true, image: 'robotshop/rs-cart:latest', key: '', logLevel: 'true', policy: 'high', requirePackageUpdate: true, timeout: 10
        }
      }
      stage('publish'){
        steps {
          twistlockPublish ca: '', cert: '', dockerAddress: 'unix:///var/run/docker.sock', ignoreImageBuildTime: true, image: 'robotshop/rs-cart:latest', key: '', logLevel: 'true', timeout: 10
        }
      }
      stage('Deploy') {
        steps {
            sh "helm upgrade --install robot-shop K8s/helm --namespace=robot-shop"
            }
        }
      }
}
