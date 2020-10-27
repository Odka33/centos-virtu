# Centos-virtu

Kickstart, Apache2, SSD, Cockpit, Icinga, Ssh, Libvirt,  # Centos-virtu

## Prérequis.

## Installation et configuration de la machine hôte.

##### Changement du hostname:

- Changement panel onlinePanel online


![](https://imgur.com/uzSRYWJ.png)


- /etc/hostname

  ```
  sudo vi /etc/hostname 
  ```
  
- /etc/host

    ```sudo vi /etc/hosts```


##### Installation de libvirt, kvm:

    sudo yum -y install libvirt libvirt-client virt-install qemu-kvm qemu-img \ syslinux syslinux-tftpboot \ centos-release-ovirt41.noarch

##### Installation de ansible:

    sudo yum -y install ansible ansible-doc
    
##### Date / Timezone:

    export LC_TIME=en_US.UTF-8
    
    tzslect
    
![](https://imgur.com/cekyW57.png)

![](https://imgur.com/3aIcfv6.png)

##### Modification des droit pour 'exploit':

- Modifié la ligne 107:
    
    ```visudo``` 
    
- Autorise tout les membres du groupe 'wheel' à utilisé sudo:

    ![](https://imgur.com/Cw4ghbZ.png)

##### Interdisez le login de root via ssh:

    vi /etc/ssh/sshd_config
    
![](https://imgur.com/IiP74FW.png)

    systemctl restart sshd.service
    
##### Création de système de fichier:
    
    /Data
    |-- /ISOs
    |-- /Vms
    `-- /web

    /applis
    `-- ansible

##### Récupérations d'un iso et mise en place d'un répo RPM:

    cd /data/ISOs
    curl -L -O http://centos.mirrors.ovh.net/ftp.centos.org/7/isos/x86_64/CentOS-7-x86_64-DVD-1810.iso
    curl -L -o sha256sum_Centos-7.txt http://centos.mirrors.ovh.net/ftp.centos.org/7/isos/x86_64/sha256sum.txt
    sha256sum -c sha256sum_Centos-7.txt 2> /dev/null
    sudo mount -o loop Centos-7-x86_64-DVD-1611.iso /mnt
    cd /data ; mkdir -p web/centos/7.1810/os/x86_64/ && ln -s 7.1810 7
    cd /mnt ; tar xvf - * | (cd /data/web/centos/7.1810/os/x86_64 ; tar xf -)
    
    


    


    

    
    
