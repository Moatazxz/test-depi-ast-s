pipeline{
agent any

tools{
   nodejs 'node24.9.0'
}
stages {
   stage ("npm buils stage")
  {
     steps {
       sh """
          npm -v
       """
       
     }

}

   stage ("build docker")
  {
     steps {
       sh """
         docker build docker.io/moatazxz/ast-test1:v1
       """
       
     }

}

   
//    stage ("push  image")
//   {
//      steps {
//        sh """
//          docker login -u moatazxz    -p 
//        """
       
//      }

// }



  
}




  
}
