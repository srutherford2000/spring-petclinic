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
        sh 'mvn sonar:sonar -Dsonar.login=sqa_bc8160d9ba8f50fe05aa2ec0a59a3046a2706e1c'
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
