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
         echo 'twist'
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
         echo ' testing '
       }
     }
     stage ('notify build result') {
       steps {
         echo 'the job is successed'
         stage ('deploy') {
       steps {
         echo 'deployment done'
         echo ' deployment complete '
       }
     }
   }
}
