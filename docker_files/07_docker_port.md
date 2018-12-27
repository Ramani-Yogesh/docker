=========================================

   
   ##**Docker Port**
 



=========================================

**Docker Port** is used to assign the port to the container.

Using below commands, You can view the ports of the containers.

        docker ps
        
            or
            
        docker container ls
        
* **Assign a Port** 

        docker container run -p 12345 -itd --name port_test httpd
        
    Here I have assign the port 12345 to the "port_test" container.
    You can view the port details using below command.

        docker port port_test
        
                or
                
        docker container port port_test