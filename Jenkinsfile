pipeline {
      agent any
    tools { maven 'maven3' }
    options {
            buildDiscarder(logRotator(numToKeepStr: '1'))
            timeout(time: 1, unit: 'HOURS')
            timestamps()
     }
    stages {
        
        stage('build'){
          
            steps{
            
                       sh 'mvn clean package'
                }
        }
    }
}
