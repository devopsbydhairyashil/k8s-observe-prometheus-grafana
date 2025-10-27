// Optional Jenkins pipeline to deploy monitoring manifests
node {
  stage('Checkout') { checkout scm }
  stage('Build exporter image') {
    sh 'docker build -t dhairyashil/custom-exporter:latest ./exporter || true'
  }
  stage('Push image') {
    withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKERHUB_USER', passwordVariable: 'DOCKERHUB_PASS')]) {
      sh 'echo $DOCKERHUB_PASS | docker login -u $DOCKERHUB_USER --password-stdin'
      sh 'docker push dhairyashil/custom-exporter:latest || true'
    }
  }
  stage('Deploy to Kubernetes') {
    sh 'kubectl apply -f manifests/'
  }
}
