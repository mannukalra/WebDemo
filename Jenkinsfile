node{
  stage ('cloning the repository'){
	git 'https://github.com/mannukalra/webdemo'
  }
  stage ('Build') {
	withMaven(jdk: 'JDK_local', maven: 'MVN_Local') {
      bat 'mvn clean package'
    } 
  }
  stage ('Tomcat Deploy') {
  	bat 'copy /Y target/webdemo.war C:/Common/apache-tomcat-8.5.32_Jenkins/webapps'
  }
  stage ("running appscan on cloud"){
      appscan application: '955fa556-8ef7-4279-8bdd-9114f5c58069', credentials: 'ASOC_Prod', name: 'SimpleIOTASOC_Test', scanner: static_analyzer('C:\\Users\\kalra_m\\eclipse-workspace\\SimpleIOT-Maven'), type: 'Static Analyzer'
  }
}
