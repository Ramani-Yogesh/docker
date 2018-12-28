=========================

  ###MYSQL

=========================

* **Pull Image**

        docker pull mysql

* **Run Containers**

        docker container run --name mysql-demo -e MYSQL_ROOT_PASSWORD=redhat -d mysql
        
    The above command create a container with name "mysql-demo", and "redhat" is a password of root, -d denotes runs in background, and finally mysql is a image name.
   
    Then you can check the container status
    
        docker container ls
        
* **Login to mysql**

    You can login from your base machine using "mysql". If you dont have "mysql", install it using following command.
    
        sudo apt-get install mysql-client
        
    Then login
    
        mysql -u root -h 172.17.0.2 -p 
        
    Here you have to mention the your container's ip. You can get your container ip from the containers details.
    
        docker inspect mysql-demo
        
    This command list all details about the container. Here you can get the ip.
    
=========================
   
   ##**HTTP or Apache**
 

=========================   

 * **Pull Image**

        docker pull httpd
        
 * **Run Containers**

        docker container run --name httpd-demo -p 8899:80 -itd httpd
        
    The above command create a container with name "mysql-demo", and "redhat" is a password of root, -d denotes runs in background, and finally mysql is a image name.

    httpd-demo ==> Container Name
    
    8080:80 ==> Host Port(8899) & Container Port(80)
            
    httpd   ==> Image Name
            
    Then you can check the container status
    
        docker container ls   
        
 * **Checking Apache**
 
    Check from your base machine
    
        curl http://localhost:8899
        
                or
                
    In Brower
    
        172.17.0.2
        
            or
            
        localhost:8899
    
    Here 172.17.0.2 is a container ip. You can check with your containers ip.
    You can get your container ip from **docker inspect con_name** command.  