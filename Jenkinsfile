pipeline{
  agent{
    label{
         label 'built-in'
         customWorkspace '/root/dockerCont1/' 
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
         sh "docker run -d -p 90:80 --name contMaster1 httpd"
         
       }
    }
    
    stage('deploy'){
       steps{
         sh "docker cp index.html contMaster1:/usr/local/apache2/htdocs"
         sh "docker exec contMaster1 chmod 755 /usr/local/apache2/htdocs/index.html"
       }
    }
  }
}




