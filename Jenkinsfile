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
