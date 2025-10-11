pipeline{
agent any

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
  {
     steps {
       sh """
         docker build -t docker.io/moatazxz/ast-test1:v1 .
       """
       
     }

}

   
   stage ("push  image")
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
     steps    {
          sshagent(credentials: ['deploy-key']) {
       sh """
              ssh -o StrictHostKeyChecking=no ubuntu@54.163.219.186  '
                  docker rm  -f "$(docker ps -aq)"
                  docker run --name myapp -p 80:80 -d docker.io/moatazxz/ast-test1:v1
              '
       """
        }
     }

}


  
}




  
}
