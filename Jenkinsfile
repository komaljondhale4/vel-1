pipeline{
  agent{
    label{
         label 'built-in'
         customWorkspace '/root/dockerCont2/' 
    }
  }
  stages{
    stage('cleaning up existing containers'){
       steps{
            // Stop all running containers
            sh "docker stop \$(docker ps -q)"
            // Remove all containers (including stopped ones)
            sh "docker rm \$(docker ps -a -q)"
       }
    }
    stage('create a container'){
       steps{
         sh "docker run -d -p 80:80 --name contMaster2 httpd"
         
       }
    }
    
    stage('deploy'){
       steps{
         sh "docker cp index.html contMaster2:/usr/local/apache2/htdocs"
         sh "docker exec contMaster2 chmod 755 /usr/local/apache2/htdocs/index.html"
       }
    }
  }
}




