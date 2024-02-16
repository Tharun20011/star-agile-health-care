pipeline {
 agent any
   stages{
      stage('code checkout'){
        steps{
          git url: 'https://github.com/Tharun20011/star-agile-health-care.git'
          echo 'Git code checkout '
        }
         }
      stage('maven packagee'){
        steps{
      
      script {
                    def mvnCmd1 = 'mvn clean'
                    def mvnCmd = 'mvn package'
                    sshagent(['ubuntu']) {
                        sh "ssh -o StrictHostKeyChecking=no ubuntu@172.31.42.130 ${mvnCmd1}"
                      sh "ssh -o StrictHostKeyChecking=no ubuntu@172.31.42.130 ${mvnCmd}"
                       
                    }
}
     }
      }
      
     
    stage('docker port expose with container'){
     steps{
      
      script {
                    def dockercmd1 = ' docker build -t sghealth-care-img . '
                    def dockerCmd = 'docker run -dt --name sghealthcon -p 8678:8678 sghealth-care-img'
                    sshagent(['ubuntu']) {
                        sh "ssh -o StrictHostKeyChecking=no ubuntu@172.31.42.130 ${dockerCmd1}"
                        sh "ssh -o StrictHostKeyChecking=no ubuntu@172.31.42.130 ${dockerCmd}"
                    }
}
}
    }
}
}
