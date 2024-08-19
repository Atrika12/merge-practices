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
     stage ('deploy') {
       steps {
         echo 'deployment done'
       }
     }
     stage ('notify build result') {
       steps {
         echo 'the job is successed'
       }
     }
   }
}
