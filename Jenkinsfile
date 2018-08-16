node{
  stage ('cloning the repository'){
	git 'https://github.com/mannukalra/webdemo'
  }
  stage ('Build') {
	withMaven(jdk: 'JDK_local', maven: 'MVN_Local') {
      bat 'mvn clean package'
    } 
  }
  stage ("running appscan on cloud"){
      appscan application: 'a242c993-a4a2-45bc-bc5f-db1d8885ce96', credentials: 'ASOC_Staging', name: 'WebDemo_0816_ISOC_Stage', scanner: static_analyzer('C:\\Users\\kalra_m\\eclipse-workspace\\webdemo'), type: 'Static Analyzer'
  }
  stage ('Tomcat Deploy') {
  	bat 'copy /Y target\\webdemo.war C:\\Common\\apache-tomcat-8.5.32_Jenkins\\webapps'
  }
}