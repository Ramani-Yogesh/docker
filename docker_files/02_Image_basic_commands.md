=========================================

   
   ##**Docker Images**
 



=========================================

* **Pull Images**

        docker pull image_name 
        
               or
               
        docker image pull image_name
        
     *__Pull Repository with multiple tags__*
    
        docker pull --all-tags image_name
        
* **List Images**

    Here you can view the image name, tag name, image id and size.

        docker images
        
   *__Show all images (default hides intermediate images)__*
    
        docker images -a
        
            or
            
        docker images --all
        
   *__To list all images in the “httpd” repository__*
        
        docker images httpd   
        
   *__List the full length image IDs__*
    
        docker images --no-trunc    
        
* **Inspect Images**

    You can also use image_id instead of image_name
    
        docker inspect httpd
        
* **Show the History of the Image**

    You can also use image_id instead of image_name

        docker history httpd
        
            or
            
        docker image history httpd
        
* **Docker Image Tag**

    It will create a copy of a image with new name

        docker image tag old_imagename:tag new_imagename:tag
        
* **Remove Image**

    You can also use image_id instead of image_name

        docker image rm httpd
        
            or
            
        docker rmi httpd
        
    *__Remove Unused Images__*
    
        docker image prune
            
    If use --all option this will remove all images without at least one container associated to them
    
        docker image prune --all
        
    *__Remove Image With force option__*
      
        docker rmi -f image_name
            
     
* **Push images**

    - #####Login to Docker Hub account
     
      Before push you need to login to your "docker hub" account
    
      It will ask the username and password of your docker hub account.
     
          docker login 
        
    - #####Tag the image(Rename)
 
      We need to tag the image(Rename)
   
          docker tag imagename:tag username_of_your_dockerhub/newimagename:tag
          
    - #####Push the Image
       
          docker push username_of_your_dockerhub/newimagename:tag
          
    - #####Logout from Docker Hub account

          docker logout

* **Save and restore images**

    *__Save images as tar file__*
    
        docker image save -o backup.tar httpd
        
     *__Load Images__*
     
     load an image from a tar archive
     
        docker load -i backup.tar
        
     After this command you can check your docker images. Then you can run 
     containers using this image.
             
 
        
           
