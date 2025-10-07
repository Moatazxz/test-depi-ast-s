pipeline{
agent any

tools{
   nodejs 'node24.9.0'
}
stages {
   stage ("login to docker hub")
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
         
       echo "buid your Image"
       """
       
     }

}

   
   stage ("deploy docker")
  {
     steps {
       sh """
         
       echo "deploy"
       """
       
     }

}



  
}




  
}
