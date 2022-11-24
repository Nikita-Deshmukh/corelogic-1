pipeline{
     agent any
       tools{
maven 'Maven-3.8.6'
}
  stages{
   stage('Git Checkout'){
    steps{
       checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'Nikita', url: 'https://github.com/Nikita-Deshmukh/corelogic-1.git']]]) 
    }   
   }
      stage('Build'){
    steps{
        sh 'mvn package -f pom.xml'
    }   
       
   }
      /*stage('Upload to Nexus'){
    steps{
        nexusArtifactUploader artifacts: [[artifactId: 'corelogic', classifier: '', file: 'target/PollSCM-Corelogic.war', type: 'war']], credentialsId: 'f3cae16c-a92f-4615-a198-bda3b71eae75', groupId: 'com.adaequare', nexusUrl: '34.132.95.253:8081/', nexusVersion: 'nexus3', protocol: 'http', repository: 'maven-snapshots', version: '1.0-SNAPSHOT'
    }   
       
   }*/
   stage('Deployment into Tomcat'){
    steps{
      deploy adapters: [tomcat9(credentialsId: '16c0e8ad-b7bb-4c4e-9f43-cdcf4eab4fc0', path: '', url: 'http://34.131.170.118:8080')], contextPath: null, war: 'target/PollSCM-Corelogic.war'  
    }   
       
   }
  }
}
