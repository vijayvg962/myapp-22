pipeline{
    agent any
    triggers {
      pollSCM '* * * * *'
    }
    
    stages{
        stage("Maven Build"){
            when {
                branch "main"
            }
            steps{
               sh "mvn package"
            }
        }
        stage("SonarQube Analysis"){
            when {
                branch "main"
            }
            steps{
               withSonarQubeEnv('sonar7') {
                    sh "mvn sonar:sonar"
               }
            }
        }
        
        stage("Nexus"){
            when {
                branch "main"
            }
            steps{
               echo "uploading artifacts to nexus...."
            }
        }
        stage("Deploy To QA"){
            when {
                branch "main"
            }
            steps{
               echo "deploying to qa server...."
            }
        }
        stage("Deploy To production"){
            when {
                branch "main"
            }
            steps{
               echo "deploying to main server...."
            }
        }
    }
}
