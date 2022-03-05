node('built-in') 
{
   stage('ContinuousDownload')
   {
      git 'https://github.com/intelliqittrainings/maven.git'
   }
   stage('ContinuousBuild')
   {
     sh 'mvn package'
   }
   stage('ContinuousDeployment')
   {
     sh 'scp /home/ubuntu/.jenkins/workspace/DeclarativePipeline1/webapp/target/webapp.war ubuntu@172.31.88.115:/var/lib/tomcat9/webapps/test1.war'
   }
  stage('ContinuousTesting')
   {
     git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
     sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
   } 
   stage('Continuousdelivery')
   {
    input message: 'Need approval from DM', submitter: 'Ravi'
    sh 'scp /home/ubuntu/.jenkins/workspace/DeclarativePipeline1/webapp/target/webapp.war ubuntu@172.31.87.155:/var/lib/tomcat9/webapps/prod1.war' 
   }
   
}
