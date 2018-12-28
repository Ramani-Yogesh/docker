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
        
        docker network create net1  
    
    *__To create a network with options__*
    
        docker network create --ip-range 192.168.10.0/24 --subnet 192.168.0.0/16 my_network1
        
    **net1** interface assigned default ip range. But the **my_network1** interface have different ip range.
    
    *__List network details__*
    
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
    
    *__Connect to Network__*
    
        docker network connect network_name con_name
        
     
        