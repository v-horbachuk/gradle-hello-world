#!groovy
flag = 0
node ("worker"){
   // Mark the code checkout 'stage'....
  stage ('Checkout')
  {
      // Get some code from a GitHub repository
      checkout scm   
  }

   // Mark the code build 'stage'....
  try 
  {
     stage ('Build Gradle')
     {
        def gradleHome = tool 'gradle4'
        sh "${gradleHome}/bin/gradle build"
     }
   } 
   catch(e) 
   {
      flag = 1
   }
    stage ('Post')
   {
     if (flag == 0)
      {
         addBadge icon: 'green.gif', id: '1', link: '', text: 'SUCCESS'
      }
     else
     {
         addBadge icon: 'red.gif', id: '2', link: '', text: 'ERROR!'
     }    
   }
}
