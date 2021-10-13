#!groovy

node ("slave1"){
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
        sh "${gradleHome}/bin/gradle clean install"
   }
   catch(Exeption e)
   {
     addErrorBadge id: '1', text: 'BUILD FAILED'
   }
    stage ('Post')
   {
      addBadge icon: '', id: '1', link: '', text: 'BUILD SUCCESS!'
     
   }
}
