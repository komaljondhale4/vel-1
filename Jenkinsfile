pipeline{
  agent{
    label{
         label 'built-in'
         customWorkspace '/root/DCont/' 
    }
  }
 stages{
   /* stage('clean containers'){
       steps{
            // Stop all running containers
            sh "docker stop \$(docker ps -q)"
            // Remove all containers (including stopped ones)
            sh "docker rm \$(docker ps -a -q)"
       }
    } */
    stage('create container'){
       steps{
         sh "rm -rf"
         sh "docker run -d -p 80:80 --name container httpd"
         
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




