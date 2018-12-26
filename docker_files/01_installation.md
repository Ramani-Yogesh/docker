=========================================

   
   ##**Docker Installation**
 



=========================================
                 



**Requirements**

To install Docker CE, you need the 64-bit version of one of these Ubuntu versions:

   _Bionic 18.04 (LTS)_

   _Xenial 16.04 (LTS)_

   _Trusty 14.04 (LTS)_

Docker CE is supported on Ubuntu on x86_64, armhf, s390x (IBM Z), and ppc64le (IBM Power) architectures.

#####Uninstall old versions

Older versions of Docker were called **docker** or **docker-engine.** If these are installed, uninstall them:

    $ sudo apt-get remove docker docker-engine docker.io
    
#####Supported storage drivers
 
 Docker CE on Ubuntu supports **overlay2** and **aufs** storage drivers.

  * For new installations on version 4 and higher of the Linux kernel, **overlay2** is supported and preferred over **aufs.**

  * For version 3 of the Linux kernel, **aufs** is supported because **overlay** or **overlay2** drivers are not supported by that kernel version.

**Install Docker CE**

You can install Docker CE in different ways, depending on your needs:

   * Most users **set up Docker’s repositories** and install from them, for ease of installation and upgrade tasks. This is the recommended approach.

   * Some users download the DEB package and **install it manually** and manage upgrades completely manually. This is useful in situations such as installing Docker on air-gapped systems with no access to the internet.

   * In testing and development environments, some users choose to use automated **convenience scripts** to install Docker.

###Install using the repository

   Before you install Docker CE for the first time on a new host machine, you need to set up the Docker repository. Afterward, you can install and update Docker from the repository.
   
   
**_SET UP THE REPOSITORY_**

1. Update the apt package index:

       sudo apt-get update

2. Install packages to allow apt to use a repository over HTTPS:

       sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
       
3. Add Docker’s official GPG key:

       curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

4. Add Repository

       $ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
       
       
####INSTALL DOCKER CE

1. Update the package 

       sudo apt-get update 
       
2. Install the latest version of Docker CE,

       $ sudo apt-get install docker-ce
     
#####To install a specific version of Docker CE, list the available versions in the repo, then select and install:

a. List the versions available in your repo:

    $ apt-cache madison docker-ce
   
b. Install a specific version by its fully qualified package name, which is package name (docker-ce) “=” version string (2nd column), for example, docker-ce=18.03.0~ce-0~ubuntu.

    $ sudo apt-get install docker-ce=<VERSION>
    
    
**Docker Group**

If you would like to use Docker as a non-root user, you should now consider adding your user to the “docker” group with something like:
   
    $ sudo usermod -aG docker user_name
      
         
