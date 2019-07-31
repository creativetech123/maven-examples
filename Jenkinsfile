node {
 
   stage('code checkout') { 
       
       git credentialsId: 'githubID', url: 'https://github.com/creativetech123/maven-examples.git'
       
   }
   
   stage('Build') {
       withMaven(jdk: 'JDK', maven: 'maven') {
    sh 'mvn clean compile'
}
     
      
   }
   
   stage('unit test') {
       withMaven(jdk: 'JDK', maven: 'maven') {
    sh 'mvn test' 
}
      
   }
 
 withSonarQubeEnv(credentialsId: 'sonarqubeid') {
    withMaven(jdk: 'JDK', maven: 'maven') {
    sh 'mvn sonar:sonar' 
 }
}
 
   stage('package') {
       withMaven(jdk: 'JDK', maven: 'maven') {
    sh 'mvn package'
}
      
   }
   
   stage('deploy to dev') {
      
   }
   
   stage('deploy to test') {
      
   }
   
   stage('deploy to prod') {
      
   }
}
