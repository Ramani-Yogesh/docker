=========================================

   
   ##**Docker CP**
 



=========================================

===> Copy files/folders between a container and the local file system.

===> Copying between containers is  not supported.

* **Local to Container**

        docker cp /home/user_name/Documents/backup con_name:/mnt

* **Container to Local**

        docker cp con_name:/root/test_dir /home/user_name/Downloads
        
        