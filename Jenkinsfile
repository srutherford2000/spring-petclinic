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
        sh 'mvn sonar:sonar -Dsonar.login=sqa_dca04b5987b2a6275847e78949727d52b1c7e644'
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
