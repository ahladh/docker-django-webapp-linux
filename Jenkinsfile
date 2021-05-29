pipeline{
  agent any
  environment {
      myEnv = ''
  }
  stages{
    stage("Build Docker Image"){
        steps{
            script{
                  myEnv = docker.build "ahladh/python:${env.BUILD_NUMBER}"
            }
        }
    }
    stage("Push Docker Image"){
        when {
          branch "master"
        }
        steps{
            script{
                docker.withRegistry('', 'Ahladh_Docker') {
                    myEnv.push()
                }
            }
        }
    }
  }
}
