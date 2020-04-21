// node {
//   currentBuild.result = "SUCCESS"

//   try {
//     stage('Prep') {
//       checkout scm
//       sh 'pwd && ls -la'
//     }

//     stage('Test'){
//       env.NODE_ENV = "test"

//       print "Environment will be : ${env.NODE_ENV}"

//       sh 'node -v'
//       sh 'npm prune'
//       sh 'npm install'
//       sh 'npm test --watchAll=false'
//     }
//   } catch(err) {
//     currentBuild.result = "FAILURE"

//     throw err
//   }
// }


pipeline {
  agent {
    docker {
      image 'node:8.12.0'
      args '-p 3000:3000'
    }
  }
  environment { 
    CI = 'true'
    HOME = '.'
  }
  stages {
    stage('Prep') {
      steps {
        checkout scm
        sh 'ls -la'
      }
    }

    stage('Test'){
      steps {
        sh 'node -v'
        sh 'npm prune'
        sh 'npm install'
        sh 'npm test --watchAll=false'
      }
    }
  }
}