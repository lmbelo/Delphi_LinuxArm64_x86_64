# Setup a Delphi Linux profile under Linux Arm64 (Ubuntu)

> **Download the SDK, deploy and run Delphi Linux x86_64 apps on Linux Arm64**

**-----> Tested on a fresh Parallels Ubuntu 22.04 Arm64 <-----**

1) **Create the Ubuntu 22.04 Arm64 virtual machine using Parallels**
    
2) **Preparing the environment**
    1) sudo apt update && sudo apt upgrade && sudo apt dist-upgrade
    2) Important: Make sure your system has been updated before proceeding

3) **Enabling the amd64 layer**
    1) Place the "amd64.list" file into "/etc/apt/sources.list.d/" to create the amd64 repository list
        - Open terminal
        - cd /etc/apt/sources.list.d/
        - sudo wget https://raw.githubusercontent.com/lmbelo/Delphi_LinuxARM64_x86_64/main/amd64.list
    2) sudo apt install -y qemu-user-static binfmt-support
    3) sudo dpkg --add-architecture amd64
    4) sudo apt update

4) **Installing x86_64 packages**
    1) Run-time common libraries:
        1) sudo apt install joe:amd64 wget:amd64 p7zip-full:amd64 curl:amd64 openssh-server:amd64 crossbuild-essential-amd64 zlib1g-dev:amd64 libcurl4-gnutls-dev:amd64 libncurses5:amd64 libasound2-plugins:amd64    
    2) GUI libraries:
        1) sudo apt install libgtk-3-dev:amd64 libcanberra-gtk-module:amd64 libcanberra-gtk3-module:amd64 

5) **Getting ready for Delphi**
    1) Create the necessary symlinks required by PAServer
        - sudo ln -s /usr/x86_64-linux-gnu/include/c++/ /usr/include/x86_64-linux-gnu/c++
        - sudo ln -s /usr/lib/gcc-cross/x86_64-linux-gnu/ /usr/lib/gcc/x86_64-linux-gnu
    2) Download and extract the PAServer - it will run under amd64
    3) Run the PAServer
        - cd {PASERVER_DIR}
        - sudo ./paserver
        - set a password or let it empty
        - type "i" to show your IP address
    4) Download the amd64 SDK in Delphi
        - create the Linux profile
        - download the SDK
        - set it as the default Linux profile
    5) Compile and deploy your app to your Linux Arm
    
6) **Debugging**
    1) Add the deadsnakes repository to install libpython3.7 
       - sudo add-apt-repository ppa:deadsnakes/ppa   
       - sudo apt-get update  
       - sudo apt install libpython3.7-dev:amd64
    2) WORK IN PROGRESS
        
7) **Warning**
    1) Don't try to install build-essential:amd64
    2) Don't try to install gcc:amd64
