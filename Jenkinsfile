pipeline{
agent any


environments {
    rig_url= "docker.io/moatazxz"
    app_name= "ast-test1"

       
}
// tools{
//    nodejs 'node24.9.0'
// }
stages {
//    stage ("npm buils stage")
//   {
//      steps {
//        sh """
//           npm -v
//        """
       
//      }

// }

   stage ("build docker")
       when {    
          branch 'main'
       }
  {
     steps {
       sh """
         docker build -t ${rig_url}/${app_name}:${BUILD_NUMBER} .
       """
       
     }

}

   
   stage ("push  image")
   when {    
          branch 'main'
       }
       
  {
     steps    {
        withCredentials([usernamePassword(credentialsId: 'dokcer_cred', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
       sh """
         docker login -u $DOCKER_USER   -p $DOCKER_PASS
         docker push docker.io/moatazxz/ast-test1:v1
       """
        }
     }

}

   stage ("Deploy")
  {

 when {    
          branch 'test'
       }
         
     steps    {

         withCredentials([usernamePassword(credentialsId: 'dokcer_cred', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {    
          sshagent(credentials: ['deploy-key']) {
       sh """
              ssh -o StrictHostKeyChecking=no ubuntu@54.163.219.186  '
                  docker login -u $DOCKER_USER   -p $DOCKER_PASS
                  docker run --name myapp -p 80:80 -d docker.io/moatazxz/ast-test1:v1
              '
       """
        }
         }
     }

}


  
}




// Variable	Description
// BUILD_NUMBER	Current build number
// BUILD_ID	Unique build ID
// JOB_NAME	Name of the job
// BUILD_URL	URL of the build
// GIT_COMMIT	Git commit hash (if applicable)
// GIT_BRANCH	Git branch name
// WORKSPACE	Job workspace directory
       




  
}
