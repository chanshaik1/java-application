pipeline {
    agent any
    tools{
        maven 'maven3.9.9'
    }

    stages {
        stage('Clone the repository ') {
            steps {
                
             git branch: 'build-and-push-to-jfrog-jenkinsfile', url: 'https://github.com/chanshaik1/java-application.git'   
                
            }
        }
       
       stage("Build the code") {
           
           steps{
               sh 'mvn clean install'
           }
       }
      stage('Push the artifacts into Jfrog artifactory') {
            steps {
              rtUpload (
                serverId: 'jfrog-server-1',
                spec: '''{
                      "files": [
                        {
                          "pattern": "*.war",
                           "target": "web-application-1/"
                        }
                    ]
                }'''
              )
          }
        }
     
        
        
        
    }
}
