#!groovy
pipeline
{
    agent
    {
        label 'worker'
    }
    tools 
    {
        gradle 'gradle4'
    }
    stages
    {
        stage ('checkout')
        {
            step ('1')
            {
                checkout scm       
            }
        }
        
        stage ('build gradle')
        {
            step ('2')
            {
                echo 'Path is' + env.PATH
                sh 'gradle build'
            }
        }
    }
    post ('failure')
    {
        failure
        {
            addBadge icon: 'red.gif', id: '1', link: '', text: 'FAILED TO INSTALL GRADLE'
        }
        success
        {
            addBadge icon: 'green.gif', id: '1', link: '', text: 'GRADLE SUCCESSFULLY INSTALLED'
        }
    }
}
// flag = 0
// node ("worker"){
//    // Mark the code checkout 'stage'....
//   stage ('Checkout')
//   {
//       // Get some code from a GitHub repository
//       checkout scm   
//   }

//    // Mark the code build 'stage'....
//   try 
//   {
//      stage ('Build Gradle')
//      {
//         def gradleHome = tool 'gradle4'
//         sh "${gradleHome}/bin/gradle build"
//      }
//    } 
//    catch(e) 
//    {
//       flag = 1
//    }
//     stage ('Post')
//    {
//      if (flag == 0)
//       {
//          addBadge icon: 'green.gif', id: '1', link: '', text: 'SUCCESS'
//       }
//      else
//      {
//          addBadge icon: 'red.gif', id: '2', link: '', text: 'ERROR!'
//      }    
//    }
// }
