pipeline{
     agent{
             label{
                     label 'built-in'
                     customWorkspace '/root/DCont4/'
                  }
          }
        
 stages{

         stage("creat container")
         {
              steps {
                      sh "docker rm -f container4 || true"
    //           sh " docker stop container4"
  //             sh " docker container rm conatiner4"
               sh " docker run -dp 91:80 --name container4 httpd"
                    }
         }

         stage("deploy index file")
         {  
              steps {
                sh " docker cp index.html container4:/usr/local/apache2/htdocs"
                sh " docker exec container4 chmod -R 777 /usr/local/apach2/htdocs"
                    }      
         }
 }
}


