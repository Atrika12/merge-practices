pipeline {
  agent any

   stages { 
     stage ( 'hello') {

       steps {
         echo 'helloworld'
       }
     }
     stage ('build') {
       steps {
         echo "build done"
       }
     }
     stage ('test') {
       steps {
         echo 'test stage done'
       }
     }
   }
}
