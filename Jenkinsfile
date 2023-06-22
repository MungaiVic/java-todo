pipeline { 
  agent any
  tools { 
    gradle "Gradle-8"
  }
  stages { 
    stage('clone repository') {
      steps { 
        git 'https://github.com/MungaiVic/java-todo'
      }
    }
    stage('Build the project') {
      steps { 
        sh 'gradle build'
      }
    }
    stage('Tests') {
      steps { 
        sh 'gradle test'
      }
    }
    stage('Deploy to Heroku') {
  steps {
    withCredentials([usernameColonPassword(credentialsId: 'heroku', variable: 'HEROKU_CREDENTIALS' )]){
      sh 'git push https://${HEROKU_CREDENTIALS}@git.heroku.com/morning-depths-56655.git master'
    }
  }
} 
  }
}
