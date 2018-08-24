node ('jenkins') {
    
  def image1
  def image2
  
  
    stage('clone repository'){
        checkout scm
    }
    
    
    stage('Build Image MariaDB'){
          image1 = docker.build("mariadb", " -f MariaDB ${WORKSPACE}") 
        
    }
    
    stage('Test Image MariaDB'){
        image1.inside {
            sh 'echo "Test MariaDB Finish"'
        }
    }
    
    stage('Build Image GLPI'){
          image2 = docker.build("glpi", " -f GLPI ${WORKSPACE}") 
        
    }
    

     stage('Test Image  GLPI'){
        image2.inside {
            sh 'echo "Test GLPI Finish"'
        }
    }



    
    stage('Push Image MariaDB'){
          
           docker.withRegistry('http://127.0.0.1:5000','3a460c76-84aa-4328-9c19-d864c4ece8b0') {
            image1.push("${env.BUILD_NUMBER}")
            image1.push("latest") 
           
         
        
        }
    }
    
    
    stage('Push Image GLPI'){
          
           docker.withRegistry('http://127.0.0.1:5000','3a460c76-84aa-4328-9c19-d864c4ece8b0') {
            image2.push("${env.BUILD_NUMBER}")
            image2.push("latest") 
         
        
        }
    }
    
            stage('list registry images to deployment on K8S '){
            sh("  docker images | grep 127.0.0.1:5000 ")
            
            }
            
            
            }
            
             

           
            
            
           
            
           
    

    
    
    

    
    
    
