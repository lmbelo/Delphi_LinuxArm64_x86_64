Preparing the environment

1) sudo apt update && sudo apt upgrade && sudo apt dist-upgrade
2) Place the "amd64.list" file into "/etc/apt/sources.list.d/"
3) sudo apt update
4) sudo apt install -y qemu-user-static binfmt-support
5) sudo dpkg --add-architecture amd64
6) sudo apt update
