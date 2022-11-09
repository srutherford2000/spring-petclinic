pipeline {
  agent any
  stages {
  
    stage('Build') {
      steps {
        sh 'mvn clean install'
      }
    }
    
    stage('Test') {
      steps {
        sh 'mvn sonar:sonar -Dsonar.login=sqa_405cabb51eeab471f9b1f4d21d14b38e7d5cc017'
      }
    }
    
    stage('Run') {
      steps {
        sh './mvnw package'
        sh 'java -jar target/*.jar &'
        sh 'echo here'
      }
    }


  }
}
