pipeline{
  agent{
    label{
         label 'built-in'
         customWorkspace '/root/DCont1/' 
    }
  }
  stages{
 /*   stage('clean containers'){
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
         sh "docker run -d -p 90:80 --name container1 httpd"
         
       }
    }
    
    stage('deploy'){
       steps{
         sh "docker cp index.html container1:/usr/local/apache2/htdocs"
         sh "docker exec container1 chmod 755 /usr/local/apache2/htdocs/index.html"
       }
    }
  }
}




