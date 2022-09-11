pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' 
            }
        }

      stage('Docker build and push') {
        steps {
          withRegistry([credentialsId: 'docker-password', url: '']) {
            sh "docker build -t mustafabalila44/sprintboot-app:${GIT_COMMIT} ."
            sh "docker push mustafabalila44/sprintboot-app:${GIT_COMMIT} ."
          }
        }
      }   
    }
}
