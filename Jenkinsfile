#!groovy
// pipeline
// {
//     agent
//     {
//         label 'worker'
//     }
//     tools 
//     {
//         gradle 'gradle4'
//     }
//     stages
//     {
//         stage ('checkout')
//         {
//             steps
//             {
//                 checkout scm       
//             }
//         }
        
//         stage ('build gradle')
//         {
//             steps
//             {
//                 echo 'Path is' + env.PATH
//                 sh 'gradle build'
//             }
//         }
//     }
//     post ('failure')
//     {
//         failure
//         {
//             addBadge icon: 'red.gif', id: '2', link: '', text: 'FAILED TO INSTALL GRADLE'
//         }
//         success
//         {
//             addBadge icon: 'green.gif', id: '1', link: '', text: 'GRADLE SUCCESSFULLY INSTALLED'
//         }
//     }
// }
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
                stage ('unit-test')
        {
                sh 'gradle test'
                junit '**/build/test-results/test/*.xml'
        }
        stage ('func-test')
        {
            def tests = ["one" : { sh "sh test-data/int-test.sh build/libs/oto-gradle-1.0.jar vaSyl 'Hello Vasyl!'"},
                     "two" : { sh "sh test-data/int-test.sh build/libs/oto-gradle-1.0.jar otoMato 'Hello Otomato!'"},
                     "tree" : { sh "sh test-data/int-test.sh build/libs/oto-gradle-1.0.jar playtikA 'Hello Playtika!'"}]
            parallel tests
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
