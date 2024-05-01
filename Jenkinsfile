pipeline {
  agent any
  stages {

    stage ('build and push') {
      steps{

        script {
          dir ('php-todo/'){
            sh 'pwd'
          docker.withRegistry('', 'DockerHub-Credential') {
            sh 'pwd'
            // def toolingImage = docker.build("warriconnected/containerization:${env.BRANCH_NAME}-v1.0.0")
            def toolingImage = docker.build("warriconnected/containerization:todo-v1.0.0")
            toolingImage.push("${env.BRANCH_NAME}-v1.0.0")
          }

          }
        }
        
      }
      
    }

// https://index.docker.io/
   
    stage('Cleanup after build') {
      steps {
        cleanWs(cleanWhenAborted: true, cleanWhenFailure: true, cleanWhenNotBuilt: true, cleanWhenUnstable: true, deleteDirs: true)
      }
    }
  }
}
