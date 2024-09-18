pipeline{
  agent any
  stages
  {
    stage('Install npm'){
      steps{
        sh 'npm install'    
      }
    }

    stage('build the project'){
      steps{
        sh 'npm run build'
      }
    }
}
}
