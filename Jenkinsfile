pipeline{
  agent { label 'java' }
  stages {
    stage ( 'checkout' ) {
      steps {
        sh 'rm -rf Bus_booking'
        sh 'git clone https://github.com/Nethravathi-R/Bus_booking.git'
      }
   }
    stage ( 'build' ) {
      steps {
        sh 'mvn --version'
        sh 'mvn clean install'        
        }      
    }
    stage ( 'deploy' ) {
      steps {
        sh 'cp /home/slave1/workspace/BusBooking/target/bus-booking-app-1.0-SNAPSHOT.jar /opt/tomcat/webapps/'
      }
    }
  }
}
