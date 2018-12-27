=========================================

   
   ##**Docker Process**
 



=========================================

* **Shows running containers**

        docker ps
        
            or
            
        docker container ps

* **Shows all containers**
        
        docker ps -a
        
            or
            
        docker ps --all


* **To see the running containers process details**

        docker container top con_name
        
                or
                
        docker  top con_name
        
* **Display the total file size**

        docker ps --size
        
            or
            
        docker ps -s
        
* **Show the latest created containers**

        docker ps --latest
        
            or
            
        docker ps -l
        
* **Show the n last created containers**

        docker ps --last
        
            or
            
        docker ps -n 2 ====> integer value
        
* **Kill the containers**

        docker kill con_name
        
* **View Live Stream**

    The below commands shows the %CPU, %Memory

        docker stats con_name 
        
        docker stats --no-stream con_name