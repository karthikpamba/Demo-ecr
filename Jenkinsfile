pipeline{
  agent any
    stages{
    
      stage("Git Checkout"){
        steps{
              git credentialsId: 'GitID', url: 'https://github.com/KPhaniPrasad/sample-java-app.git'
        }
      }
      
      

      stage("Maven Build"){
      steps{
          sh "mvn clean package"
  
    }
}


  
    stage("Docker Build image and Tag"){
            steps{
                  sh 'docker image build -t $JOB_NAME:v1.$BUILD_ID .'
                  sh 'docker image tag $JOB_NAME:v1.$BUILD_ID dockersandheep/$JOB_NAME:v1.$BUILD_ID'
            }
            }
            
     stage("Push image to Docker Hub"){
            steps{
                  withCredentials([string(credentialsId: 'DockerHpwd', variable: 'DockerHubPwd')]) {
                  sh 'docker login -u karthikpamba -p Ruchika@1999'
                  sh 'docker push karthikpamba/$JOB_NAME:v1.$BUILD_ID'
            }   
            }
            }  


      
    }

  
}
