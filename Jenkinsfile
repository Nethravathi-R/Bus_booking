pipeline{
  agent { label 'java' }
  stages {
    stage ( 'checkout' ) {
      steps {
        sh 'git clone https://github.com/Nethravathi-R/Bus_booking.git'
      }
   }
    stage ( 'build' ) {
      steps {
        sh 'mvn --version'
        sh 'mvn clean install'        
        }      
    }
  }
}
