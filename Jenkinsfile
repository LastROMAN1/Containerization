
pipeline {
  agent any
  stages {

    stage ('build and push') {
      steps{

        script {
          dir ('tooling/'){
            sh 'pwd'
          docker.withRegistry('', 'a9959bb4-49b6-4f96-b62d-0f6a8c801076') {
            sh 'pwd'
            // def toolingImage = docker.build("warriconnected/containerization:${env.BRANCH_NAME}-v1.0.0")
            def toolingImage = docker.build("warriconnected/containerization:tooling-v1.0.0")
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







