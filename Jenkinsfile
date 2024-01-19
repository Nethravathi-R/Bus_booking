pipeline	{
    agent	{
        label 'java'
    }

        stages {
        stage('checkout')	{	
            steps	{
				sh 'rm -rf Bus_booking'
				sh 'git clone https://github.com/Nethravathi-R/Bus_booking.git'
				}
			}

        stage('build') {
        steps 	{
                script 	{
                    sh 'mvn --version'
                    sh 'mvn clean install'
                }
            }
		}
		
		stage("SonarQube analysis")	{
            steps 	{
                withSonarQubeEnv('sonar')	{
                    sh 'mvn clean package sonar:sonar'
				}
            }
        }		

                
        stage ( 'deploy' )	{
		steps 	{
				sh 'ssh root@172.31.46.40'
				sh 'scp /home/slave1/workspace/BusBooking/target/bus-booking-app-1.0-SNAPSHOT.jar root@172.31.46.40:/opt/apache-tomcat-8.5.98/webapps'
                }
			}
        }
	
       
        post	{	
        success {
            echo "Build, Run, and Deployment to Tomcat successful!"
        }
        failure {
            echo "Build, Run, and Deployment to Tomcat failed!"
        }
    }
}
