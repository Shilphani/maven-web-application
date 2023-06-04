node{
    
def mavenHome = tool name: 'maven3.9.2'
echo "Job name is: $JOB_NAME"
echo "Node name is: $NODE_NAME"
echo "Jenkins Home URL is: $JENKINS_HOME"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
    
stage('CheckOutCode'){
 git credentialsId: '34118604-aa32-49c7-b9d7-c026f60ea661', url: 'https://github.com/Shilphani/maven-web-application.git'       
    }

stage('Build'){
   sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReport'){
    sh "${mavenHome}/bin/mvn clean sonar:sonar"
}
stage('UploadArtifactsIntoNexus'){
    sh "${mavenHome}/bin/mvn clean deploy"
}
stage('DeployAppIntoTomcatserver'){
    sshagent(['459ccd70-c09d-4a9c-99cb-83381b9451f5']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@65.2.78.117:/opt/apache-tomcat-9.0.75/webapps/"    
    }

}
*/
}
