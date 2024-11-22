pipeline{
  agent{
    label{
         label 'built-in'
         customWorkspace '/root/dockerCont3/' 
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
         sh "docker run -d -p 8001:80 --name contMaster3 httpd"
         
       }
    }
    
    stage('deploy'){
       steps{
         sh "docker cp index.html contMaster3:/usr/local/apache2/htdocs"
         sh "docker exec contMaste3r chmod 755 /usr/local/apache2/htdocs/index.html"
       }
    }
  }
}




