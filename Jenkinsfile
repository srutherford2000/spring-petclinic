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
        sh 'mvn sonar:sonar -Dsonar.login=sqa_bc8160d9ba8f50fe05aa2ec0a59a3046a2706e1c\''
      }
    }

    stage('Run') {
      parallel {
        stage('Run on This Server') {
          steps {
            sh './mvnw package'
            sh 'java -jar target/*.jar'
          }
        }

        stage('Run on The Other Server') {
          steps {
            ansiblePlaybook 'my_playbook.yml'
          }
        }

      }
    }

  }
}