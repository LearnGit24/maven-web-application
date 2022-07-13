node
{

def mavenHome = tool name: "maven3.8.6"
properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '5', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

echo "The Job name is : ${env.JOB_NAME}"
echo "The node name is : ${env.NODE_NAME}"
echo "The WSpace path name is : ${env.WORKSPACE}"
echo "The node label is : ${env.NODE_LABELS}"
echo "The build number is : ${env.BUILD_NUMBER}"

stage('CheckoutCode')
{
git branch: 'development', credentialsId: '003c4ea1-0ddf-423d-b9bc-ff10e310fb99', url: 'https://github.com/LearnGit24/maven-web-application.git'
}


stage('Build')
{
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReport')
{
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('UploadArtifactsIntoNexus')
{
sh "${mavenHome}/bin/mvn deploy"
}

stage('DeployToTomCat')
{
sshagent(['e4b5afa4-1970-4d51-8e1e-a2fb39f04dd7']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.126.200.76:/opt/apache-tomcat-9.0.64/webapps/"
}

}
*/


}

