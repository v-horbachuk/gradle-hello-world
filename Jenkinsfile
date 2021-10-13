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
        sh "${gradleHome}/bin/gradle gradle build"
     }
   } 
   catch(e) 
   {
     addErrorBadge id: '1', text: 'BUILD FAILED!'
   }
    stage ('Post')
   {
      addBadge icon: 'icon.svg', id: '2', link: 'https://www.google.com/search?q=icon+green&rlz=1C5CHFA_enUA973UA973&sxsrf=AOaemvL8W7EjqoFY9-WDzENchV_mjhOCig:1634132297356&tbm=isch&source=iu&ictx=1&fir=Jp2NT_nmlkjFfM%252CRK9tCJK0ogEYEM%252C_%253Bgw3_Glz3HTY81M%252CyqyK36ly4ncKdM%252C_%253BUeUppuTrPXCg2M%252CcQ8hJRBZInhjCM%252C_%253BAepSiQERTZQe5M%252ClWCB_VBiDDhJxM%252C_%253Bwia--dGR6LZE-M%252CtwtYNaZsXZgVyM%252C_%253BHkOiT-wi8N-h8M%252CRK9tCJK0ogEYEM%252C_%253Ba-VQIp_KhmYjaM%252CMKAEQgrsmBGnHM%252C_%253BL0qMkz4iQJrcYM%252CovPrKbAxLSDVyM%252C_%253BUhjbyyjRusQaxM%252CIT6eJt1IglThBM%252C_%253B5totvs3e4Z7mJM%252CZREByy4PlvTdIM%252C_%253ByQN2NGbwdBGs1M%252CJdvFvFa7HLSraM%252C_%253BC5We3ZkJCGIFIM%252C8fZGoHT7saRzCM%252C_%253BQgWOjsExEw4ftM%252CZ0SljfLEFqAnrM%252C_%253Bw3pOeRCQQE3c3M%252CRw2etYs6GgBJgM%252C_%253BE7LX7RpryaUWkM%252CxjgXhqgKU9UrYM%252C_%253BEvqhbTz20FxePM%252CvtUfOC5uolEs0M%252C_%253BJ1OmgysSpnoNuM%252Cay-RYb5UMf105M%252C_&vet=1&usg=AI4_-kRG0K-hTAZ5XZPg1B_6C-_Pi8l9xA&sa=X&ved=2ahUKEwjq2uWYwcfzAhUFyKQKHc0oBH4Q9QF6BAgREAE#imgrc=Jp2NT_nmlkjFfM', text: 'BUILD SUCCESS!'
     
   }
}
