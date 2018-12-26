=========================================

   
   ##**Docker Containers**
 



=========================================

* **List Containers**  
    
    *__List running containers__*
     
        docker container ls
        
    *__List all containers__*
   
        docker container ls -a 
        
            or
            
        docker container ls --all
      
* **Run Containers**

    "**Run**" command is used to run a container from image. You can run multiple
    containers from single image. If you run a container multiple times from image 
    everytime it will create a new container.

    Use this command to run a container. It will create a new container 
    with random name and login directly.    
        
        docker container run -it image_name
        
                or
                
        docker run -it image_name
        
    Use this command, It will create a new container with name 'test' and
    login directly
   
        docker container run --name test -it image_name
        
    Use this command, It will create a new container with name 'test1' and
    login automatically, once you exit from the container, it will remove 
    automatically.
   
        docker container run --name test1 --rm -it image_name
         
* **Start and Stop Containers**

    Once you exit from container, it will be going to stop. You can start or
    stop the containers.
    
     *__Start the containers__*
        
        docker container start con_name
            
                or
                
        docker start con_name
    
    This command first start the container, then login directly 
    to that container.
    
        docker container start -ia con_name
        
                or
                
        docker  start -ia con_name
      
     *__Stop the containers__*  
        
        docker container stop con_name
            
                or
                
        docker stop con_name

* **Attach Containers**

    You can login to the existing container, using attach command.
    If you want to attach the container, that container must in 
    running stage.

        docker container attach con_name 
        
* **Create Containers**

    This command is used to create  a container. You can check the 
    container status using "**docker container ls -a**"
    
        docker create -it image_name
            
                or
                
        docker container create -it image_name

    You can also mention the name of the container.
    
        docker create -it --name=con_name image_name
        
                or
        docker container create -it --name=con_name image_name
        
    After you create a container, this is in "created" stage.(You 
    can check **docker container ls -a**), If you want to login,
    use the following commands
    
        docker start -ia con_name
        
                or
                
        docker start con_name
        
        docker container attach con_name
                        
* **Inspect Containers**        
   
    This command is used to get  all details of the container.
    
        docker inspect con_name
        
                or
                
        docker container inspect con_name

* **View logs of Containers**        
           
        docker logs con_name
        
                or
                
        docker container logs con_name
 
* **Rename Containers**   
 
        docker container rename old_con_name new_con_name
        
                or
                
        docker rename old_name new_name   

* **Remove Containers**        

        docker container rm con_name
        
                or
                
        docker rm con_name
        
* **Prune Containers**
       
        docker system prune
        
    This will remove all stopped container, all dangling images,
    all volumes not used by at least one container.
    
* **Pause and unpause Containers**  
   
        docker pause con_name
        
        docker unpause con_name
        
* **Import/Export Containers**

    After import the tar file, it will create as a image. Then
    you will run a container from that image

    *__Export containers__*        

        docker export -o backup.tar con_name
        
    *__Import containers__*
   
        docker import /path/backup.tar new_image_name:tag
    
    *__Run containers from Imported Images__*
    
    If you want to access the information within the container, 
    or just want to create a container based on an imported image 
    you can do it givin it an entrypoint command.
    
        docker container run -it new_image_name:tag bash
        
                or
                
        docker container run -itd --entrypoint=bash new_image_name:tag
        
    This is because what the export/import command does, it just 
    saves the filesystem, this means it will remove the entrypoint 
    command as well as its history and the layers of the built container,
    effectively flattening the image.
    
    *__Import from Remote location__*
    
        docker import http://example.com/backup.tar new_image_name:tag
        
    *__Import with comment__*   
    
        docker import -m "message" /path/backup.tar new_image_name:tag