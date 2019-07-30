node {
    stage('Code Checkout') { // for display purposes
     echo 'Checout Code and clone it inside jenkins workspace.'
     git 'https://github.com/creativetech123/sonar-maven.git'
   }
   stage('Build Test & Package') {
      echo 'Build the package'
      withMaven(jdk: 'JDK', maven: 'maven') {
       sh 'mvn clean install'
     }
   }
   stage('SonarScan') {
      //withSonarQubeEnv('SonarQube') {
        withMaven(jdk: 'JDK', maven: 'maven') {
             //sh 'mvn clean package sonar:sonar' 
            sh 'mvn clean compile sonar:sonar -Dsonar.projectKey=maven-project -Dsonar.organization=creativetech123 -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=e130fab062012d5160ab51a8ee03561c457e0268'   
         //}
      }
   }
   stage('Artifacts') {
       echo 'package the project artifacts..'
       withMaven(jdk: 'JDK', maven: 'maven') {
       sh 'mvn package'
     }
   
   }
   stage('Deploy to Dev'){
       echo 'Deploy to Dev environment'
   }
   stage('Deploy to Test'){
       echo 'Deploy to Test environment'
   }
      stage('Test Automation'){
       echo 'Deploy to Dev environment'
   }
   
}
