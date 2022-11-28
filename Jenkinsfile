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
        sh 'mvn sonar:sonar -Dsonar.login=sqa_ee7ba11c2c647ccc53e12f5d8b90303e95726dfc'
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
            sh 'ansible-playbook /etc/ansible/my_playbook.yml'
          }
        }

      }
    }

  }
}
