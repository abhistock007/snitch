pipeline {
	agent any
	
	stages {
	    stage('Checkout') 
              {
	        steps 
                     {
			checkout scm			       
		      }}
		stage('Build') {
	           steps {
			  sh '/home/ubuntu/Downloads/apache-maven-3.6.0/bin/mvn install'
	              }}
		stage('Deployment'){
		    steps {
			
			sh 'cp /home/ubuntu/Documents/grras/snitch/target/snitch.war /home/ubuntu/Downloads/apache-tomcat-9.0.71/webapps'
	              }}
}
post
{
always
{
slackSend channel: 'slacknotification', message: 'Please find the pipeline status below ${env.JOB_NAME} ${env.BUILD_NUMBER} ${env.BUILD_URL}'
}
}
}
