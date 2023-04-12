node{

echo "The job name is : ${JOB_NAME}"
echo "The Build number is : ${BUILD_NUMBER}"
echo "The node name is : ${NODE_NAME}"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '5', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
    
def mavenHome = tool name: 'Maven3.9.0'

stage('checkout'){
git branch: 'development', credentialsId: 'b0a4be40-945a-495d-9b3a-2b0c11723fd0', url: 'https://github.com/vineethreddydesireddy/maven-web-application.git'
}

stage('build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('UploadArtifactintoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}

stage('DeployAppintoTomcat'){
sshagent(['1342c8f1-4feb-4fed-bb00-d0485a83d61e']) {
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.44.215:/opt/apache-tomcat-9.0.73/webapps/"
}
}
*/
}
