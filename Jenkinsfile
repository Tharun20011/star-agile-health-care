pipeline {
   agent any
   stages {
       stage('Git Checkout') {
           steps {
               git url: 'https://github.com/Tharun20011/star-agile-health-care.git'
               echo 'Git code is cloned'
           }
       }
     stage('Maven clean') {
           steps {
               sh 'mvn clean'
           }
       }
     stage('Maven package') {
           steps {
              sh 'mvn package'
           }
       }
     stage('Docker Image') {
           steps {
               sh 'docker buildx build -t tharunselvarangam/medicureimgcapstone . '
           }
       }
       stage('Docker push') {
           steps {
               sh 'docker push tharunselvarangam/medicureimgcapstone  '
           }
       }
       
     stage('K8s deployment') {
           steps {
               sh 'kubectl apply -f healthpod.yml '
           }
       }
       
       
       
   }
}
