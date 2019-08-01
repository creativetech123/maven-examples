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
stage("Quality Gate"){
          timeout(time: 1, unit: 'HOURS') {
              def qg = waitForQualityGate()
              if (qg.status != 'OK') {
                  error "Pipeline aborted due to quality gate failure: ${qg.status}"
              }
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
