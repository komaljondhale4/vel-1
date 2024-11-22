pipeline{
  agent{
    label{
         label 'built-in'
         customWorkspace '/root/DCont3/' 
    }
  }
  stages{
    stage('clean containers'){
       steps{
            // Stop all running containers
            sh "docker stop \$(docker ps -q)"
            // Remove all containers (including stopped ones)
            sh "docker rm \$(docker ps -a -q)"
       }
    }
    stage('create container'){
       steps{
         sh "docker run -d -p 8001:80 --name container3 httpd"
         
       }
    }
    
    stage('deploy index file'){
       steps{
         sh "docker cp index.html container3:/usr/local/apache2/htdocs"
         sh "docker exec container3 chmod 755 /usr/local/apache2/htdocs/index.html"
       }
    }
  }
}




