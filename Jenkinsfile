pipeline{
    agent
    {
        docker
        {
             image 'maven:3.6.3-jdk-11'
             args '-v /root/.m2:/root/.m2'
        }
    }
   
  stages
  {
     
    stage('Compile')
      {
          steps{
              sh 'java -version'
              sh 'mvn compile'
          } 
      }
    stage('Sonar Analysis')
    {
        agent any
        steps
        {
            withSonarQubeEnv('sonarToken')
            {
                 sh 'java -version'
                 sh 'mvn clean package sonar:sonar'
            }
        }
    }
  }
}
