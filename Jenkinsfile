node{
def mavenHome = tool name: 'maven3.8.7'
//CheckoutCode from git
stage('CheckoutCode'){
git branch: 'development ', credentialsId: 'c7f25b29-2361-4b40-9dbc-74c082209e41', url: 'https://github.com/amazonmarts/maven-web-application.git'
}

//Build
stage('Build')
{
  sh "${mavenHome}/bin/mvn clean package"
}

//Execute SonarQube report
stage('ExecuteSonarQubeReport')
{
 sh "${mavenHome}/bin/mvn sonar:sonar"
}
*/
//UploadArtifacts into Nexus
stage('UploadArtifactsIntoNexus')
{
 sh "${mavenHome}/bin/mvn deploy" 
}

//Deploy application into tomcat server
stage('DeployApp')
{
sshagent(['de632d04-273c-4f8e-8ae5-bdbeeca4703e']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.109.184.80:/opt/apache-tomcat-9.0.73/webapps"
}
}*/
}//node closing
