pipeline{
        agent{
           label{
               label 'built-in'
               customWorkspace '/root/DCont/' 
                }
              }
    stages{
       stage('clean workspace'){
           /* steps{
                   sh "rm -rf /DCont"
                 } 
                                  }  */
         stage('create container'){
             steps{
                      sh "docker rm -f container2 || true"
                 /* sh "docker stop container"  
                  sh "docker rm container" */
                  sh "docker run -dp 80:80 --name container httpd"
                  }
                                  }
     
          stage('deploy'){
             steps{
                sh "docker cp index.html container:/usr/local/apache2/htdocs"
                sh "docker exec container chmod 755 /usr/local/apache2/htdocs/index.html"
                  }
                        }
           }
   }




