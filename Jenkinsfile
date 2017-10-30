node {
   def mvnHome
   def version 
   stage('Preparation') {
      git 'https://github.com/SterlingTraining/addressbook.git'
      mvnHome = tool 'maven4'
	  version = '3.3.9' 
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
	 stage('DeployToServer') {
	 }
} 
