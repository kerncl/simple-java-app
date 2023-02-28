
pipeline {

  agent any

  tools {
    maven 'jenkins-maven' 
  }

  stages {
  
    stage('Build') {
      steps {
        sh 'mvn clean package'            
      }
    }
    
    stage('Test') {
      steps {
        sh 'mvn test'            
      }
    }    
    
    stage('Deploy') {
      steps {
        sh 'java -jar target/my-app-1.0-SNAPSHOT.jar'
      }
    }

    stage('Archive') {
      steps {
        archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false, onlyIfSuccessful: true
      }
    }

    stage('Dummy') {
        steps {
            echo 'Meaningless statement to verify this'
    }
}
    
  }
    
  post {
    always {
      junit(
        allowEmptyResults: true,
        testResults: 'target/surefire-reports/*.xml'
      )
    }
  }     
    

}


