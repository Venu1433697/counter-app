pipeline{
  agent any

  stages
  {
    stage('Install npm'){
      steps{
        bat 'npm install'    
      }
    }

    stage('build the project'){
      steps{
        bat 'npm run build'
      }
    }
    
  }
}
