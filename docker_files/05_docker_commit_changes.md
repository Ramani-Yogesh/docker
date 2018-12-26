=========================================

   
   ##**Docker Commit**
 



=========================================

* **Log into container**

        docker container run -it ubuntu
        
    Install and configure anything you want and quit from 
    container
    
* **Commit Changes**

        docker container commit -m "message" con_name new_image_name
        
* **Verify the image is created**

        docker images
        
* **Log into container using new_image**

        docker run -it new_image_name
        
* **Check the changes**

    Check all the things before you have done.          