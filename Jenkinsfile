pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'compiling the code for sysfoo app.....'
        sh 'mvn compile'
      }
    }

    stage('test') {
      parallel {
        stage('test') {
          steps {
            echo 'running the unit tests...'
            sh 'mvn clean test'
          }
        }

        stage('stage1') {
          steps {
            sleep 5
          }
        }

        stage('stage2') {
          steps {
            sleep 9
          }
        }

        stage('stage3') {
          steps {
            sleep 19
          }
        }

      }
    }

    stage('package') {
      steps {
        echo 'step 3'
        sh 'mvn package -DskipTests'
        archiveArtifacts 'target/*.war'
        sleep 3
      }
    }

  }
  tools {
    maven 'Maven 3.6.3'
  }
  post {
    always {
      echo 'genrating artifacts...'
    }

  }
}