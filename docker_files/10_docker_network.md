=========================================

   
   **Docker Network**
 

=========================================

* **List Network**
    
     - To list all networks
     
           docker network ls
     
     - To display the full network id
     
           docker network ls --no-trunc
        
     - Filter
     
     In filter option you can filter multiple flags like  **driver, id, label, name, scope, type**
        
          docker network ls  -f id=0ab7c4bebe0b   
        
* **Create Network**

    - The default network(interface) is **_bridge_**
    
    - If you are creating a new container, it is automatically connect with bridge network.

    *__To create a network__*
        
        docker network create  my_network1
    
    *__To create a network with options__*
    
        docker network create --ip-range 192.168.10.0/24 --subnet 192.168.0.0/16 my_network2
        
    **my_network1** interface have default ip range. But the **my_network2** interface have different ip range.
    
    *__List network details__*
    
        docker network inspect my_network1
        
                or
        
        docker inspect my_network1 
        
    Here you can see the all details about that interface. You can see the network range and everything.
    
    If you want to run a container with the new interface, the container have a that interface ip range.
        
* **Connect/Disconnect Network**

    - Once you are creating a new container, it is connecting with "bridge" network.
    
    - You can connect your container with another interface.
    
    - You can connect your container with multiple interface.
    
    - So, single container can have multiple ips.
    
    - You can also disconnect from particular network.
    
    - You can also assing static ips to container.
    
    - User specified IP address(Static IP) is supported on user defined networks only
    
    *__Connect to Network__*
    
        docker network connect network_name con_name
    
    *__Disonnect from Network__*    
        
        docker network disconnect network_name con_name    
     
    *__Example__*
    
        docker network connect my_network1 test_container
        
        docker network connect my_network2 test_container
        
    Check the ip details:
    
        docker inspect test_container
        
                or 
                
        docker inspect my_network1
      
        docker inspect my_network2
        
    - **docker inspect my_network1** this command shows which containers are connected with that network.
    
    - **docker inspect test_container** This command shows which networks are connected with that container.
    
* **Assign Static IPs**

    *__Create a Network__*
    
        docker network create --ip-range 10.10.0.0/24 --subnet 10.0.0.0/16 my_network3
        
    *__Connect to Network__*    
     
        docker network connect --ip 10.10.0.9 my_network3 demo_container
        
    *__Check the ip__*
    
        docker container inspect demo_container
        
    Here you can see 2 ips. One ip from default network "bridge", and another ip from "my_network3"
    
  - You can also connect to the network when you create a container     
        
        docker container run -itd --name test1 --network=my_network1 httpd
        
                    or
                    
        docker container run -itd --name testing --network=my_network1 --ip 10.0.0.8 httpd     
    
  - If you assign the network when create a container, this will not connect with the default network "bridge".
  
* **Remove Network**

        docker network rm network_name
        
        docker network prune
        
The above command remove all unused networks & not used by atleast one container.

* **Set HostName**

        docker container run -it --name con_name --hostname test.example.com image_name
        
    (Check the Hostname)
   
* **Link Containers**    

        docker container run -itd --name test1 --hostname test1.example.com ubuntu
        
        docker container run -itd --name test2 --hostname test2.example.com --link test1:t1 ubuntu
        
   - Here I have created 2 containers. 
   
   - The test2 container have a link with test1.
   
   - Source container is test1. Alias name is t1
   
   - Image name is ubuntu.
   
   - The 'test1' container should connect with default network "**bridge**"
   
        
        docker container attach test2
        
        [root@34873294732847]# cat /etc/hosts
        
   (Here you can see the "test1" container's host entry)
        
        [root@34873294732847]# ping test1.example.com
        
   (It will ping)
   

   * **Checking link details**
   
        
        docker inspect -f "{{ .HostConfig.Links }}" test2
        
   It will show the output like below:
   
        [/test1:/test2/t1]
   
- Here, 
   
   test1 --> Source Container Name
   
   test2 --> Linked Container
        
   t1    --> Alias Name
    

    