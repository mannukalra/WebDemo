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
  	bat 'copy /Y target\\webdemo.war C:\\Common\\apache-tomcat-8.5.32_Jenkins\\webapps'
  }
  stage ("running appscan on cloud"){
      appscan application: 'cbbc6349-3293-46f0-94ec-2df22fb254ae', credentials: 'Ananth_ISOC_Prod', name: 'WebDemoPL_0809Ananth_ISOC_Prod', scanner: static_analyzer('C:\\Users\\kalra_m\\eclipse-workspace\\webdemo'), type: 'Static Analyzer'
  }
}
+