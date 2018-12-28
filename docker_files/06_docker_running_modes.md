=========================================

   
   **Docker Running Modes**
 

=========================================

* **Detached Mode**

    It means that a container runs in the background of your terminal.
    
        docker container run -itd ubuntu
        
    check the container status. Now this container is in Up status.
        
        docker ps
        
            or
            
        docker container ls
        
* **Exec Mode**

    Docker **exec** is commonly used CLI command that allows you to run a 
    command within an existing running container
        
        docker exec -d con_name commands
        
    **_Example 1_**
    
        docker exec -d test_container touch /root/file1.txt
        
    The above command executes the output in background of your terminal.
    
     **_Example 2_**
     
          docker exec -it test_container ping google.com          
    
    The above command executes the output on the screen.
    
    **-d**  ---> Running as a background process
    
    **-it** ---> Running as a foreground process
    
* **Attach Mode**

    You can login to the existing container, using attach command.
    If you want to attach the container, you need to start the container.
    
    **1** First run a container in background mode
    
            docker container run -itd ubuntu
            
    **2** Check the Container status
    
            docker ps
            
    **3** Attach the container
    
            docker container attach con_name
        
        
        