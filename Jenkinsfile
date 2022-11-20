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
        sh 'mvn sonar:sonar -Dsonar.login=sqa_48e6a40a6af4da348a67ff423c58586628315f03'
      }
    }
    
    stage('Run') {
      steps {
        sh './mvnw package'
        sh 'java -jar target/*.jar'
      }
    }


  }
}
