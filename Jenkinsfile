pipeline
{   agent 
 {
	 label 'Nodes'
 }
    tools 
    {
        maven 'Maven 3.8.2'
    }
    stages
    {
        stage('CheckOutCode')
        {
            steps
            {
                git branch: 'master', credentialsId: '32894d77-9108-40d7-86ba-5ea7178c1da4', url: 'https://github.com/tpk-hyd/maven-web-application.git'
	        }
         }
    
        stage('Build')
        {
            steps
            {
                sh "mvn clean package"
            }
        }
        stage('DeployAppIntoTomcat')
        {
          steps
            {
                sshagent(['9a6d4398-6d54-4451-a04e-041ad16cc0c5']) 
                {
                    sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/17JUNE-DECLERATIVEWAY/target/maven-web-application.war ec2-user@172.31.38.230:/opt/tomcat9/webapps/"    
                }
            }
        }
    }
}

/*
node
{
    stage('CheckOutCode')
    {
        git credentialsId: '32894d77-9108-40d7-86ba-5ea7178c1da4', url: 'https://github.com/tpk-hyd/maven-web-application.git'  
    }
    stage('BuildProject')
    {
        def mavenHome = tool name:'Maven 3.8.2'
        sh "${mavenHome}/bin/mvn clean package"
    }
    stage('Deploy')
    {
        sshagent(['f9792aae-573b-42f1-9496-053334fecb35'])
        {
            sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/16JUNE-SCRIPTED/target/maven-web-application.war ec2-user@172.31.38.230:/opt/tomcat9/webapps/"
        }
    }
}
*/

/* 
pipeline{

agent any

tools{
maven 'maven3.8.2'

}

triggers{
pollSCM('* * * * *')
}

options{
timestamps()
buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5'))
}

stages{

  stage('CheckOutCode'){
    steps{
    git branch: 'development', credentialsId: '957b543e-6f77-4cef-9aec-82e9b0230975', url: 'https://github.com/devopstrainingblr/maven-web-application-1.git'
	
	}
  }
  
  stage('Build'){
  steps{
  sh  "mvn clean package"
  }
  }
  //Pipeline closing
/*
 stage('ExecuteSonarQubeReport'){
  steps{
  sh  "mvn clean sonar:sonar"
  }
  }
  
  stage('UploadArtifactsIntoNexus'){
  steps{
  sh  "mvn clean deploy"
  }
  }
  
  stage('DeployAppIntoTomcat'){
  steps{
  sshagent(['bfe1b3c1-c29b-4a4d-b97a-c068b7748cd0']) {
   sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@35.154.190.162:/opt/apache-tomcat-9.0.50/webapps/"    
  }
  }
  }
  
}//Stages Closing
*/
/* 
post{

 success{
 emailext to: 'devopstrainingblr@gmail.com,mithuntechnologies@yahoo.com',
          subject: "Pipeline Build is over .. Build # is ..${env.BUILD_NUMBER} and Build status is.. ${currentBuild.result}.",
          body: "Pipeline Build is over .. Build # is ..${env.BUILD_NUMBER} and Build status is.. ${currentBuild.result}.",
          replyTo: 'devopstrainingblr@gmail.com'
 }
 
 failure{
 emailext to: 'devopstrainingblr@gmail.com,mithuntechnologies@yahoo.com',
          subject: "Pipeline Build is over .. Build # is ..${env.BUILD_NUMBER} and Build status is.. ${currentBuild.result}.",
          body: "Pipeline Build is over .. Build # is ..${env.BUILD_NUMBER} and Build status is.. ${currentBuild.result}.",
          replyTo: 'devopstrainingblr@gmail.com'
 }
 
}


}//Pipeline closing
*/
