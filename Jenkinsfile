pipeline {
 agent any
   stages{
      stage('code checkout'){
        steps{
          git url: 'https://github.com/Tharun20011/star-agile-health-care.git'
          echo 'Git code checkout "
        }
         }
      stage('maven test'){
        steps{
          sh 'mvn test'
        }
     }
      stage('Maven package'){
        steps{
        sh 'mvn package'
        }
}
      stage('docker file build'){
        steps{
        sh 'docker build -t sghealth-care-img . '
        }
}
    stage('docker port expose with container'){
      steps{
        sh 'docker run -dt --name sghealthcon -p 8678:8678 sghealth-care-img '
      }
}
}
}
