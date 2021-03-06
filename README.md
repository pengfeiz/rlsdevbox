# rlsdevbox

A vagrant box for development

## Instructions

### Pre-requisites

Make sure that all the requirements are present

- [Vagrant](https://www.vagrantup.com/downloads.html)
- [Virtualbox](https://www.virtualbox.org/wiki/Downloads)
- Ansible (via [Homebrew](http://brew.sh/))

    ```sh
    # fresh install
    $brew update
    $brew install ansible

    # update
    $brew update
    $brew upgrade ansible
    ```

- Passlib 

    ```sh
    $sudo pip install passlib
    ```

- Vagrant docker-compose provisioner plugin

    ```sh
    $vagrant plugin install vagrant-docker-compose
    ```

- RSA Key(**If you already have your key in ~/.ssh/, you don't need to generate**)

    Generate a private/public rsa keypair for your devbox
    ```sh
    $ssh-keygen -t rsa 
    ```

### Getting started

1. Start the vagrant box

    ```sh
    #change directory to where the Vagrantfile is, and then
    $vagrant up
    ```

2. Provision the vagrant box

    ```sh
    # get the latest version of the ansible roles
    $ansible-galaxy install -f -r requirements.txt

    # provision with ansible
    # vault-pass will be given by a rls dev
    # username & password prompt are for the username/password you wish to use. It's
    # easiest to choose the same username as that on the host machine
     $ansible-playbook -i vagrant provision.yml -u vagrant --sudo
    ```

3. Connect to your freshly installed and provisioned vagrant dev machine

    ```
    ssh 192.200.200.200
    ```

4. Enjoy, and tweak as you wish

### Recommended

- Add the following line to your `/etc/hosts` file, for easy ssh, and consistent resolution

    ```
    192.200.200.200  devbox
    ```
