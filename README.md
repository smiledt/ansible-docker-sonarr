NFS-Client
=========

A small role to mount NFS shares on my Linux virtual machines. 

Requirements
------------

You need to have a NFS share on the network, and the ability to mount it via dns or IP address. 

Role Variables
--------------

Required variables are listed here, along with default values (specific to my environment, see fefaults/main.yml).

    mnt_path: /mnt/storage

This is the local directory on the host. If this directory does not exist, it will be created during runtime.

    nfs_host: nas.domain.com

This is the address of the NFS server. This can either be a resolvable FQDN or an IP address.

    share_path: /mnt/1tb_mirror

This is the exported NFS share on the server.  

Dependencies
------------

None.

Example Playbook
----------------

    - name: Connect the vm to the Media share on my TrueNAS vm.
      hosts: nfs_client_media
      become: true
      vars:
        nfs_mounts:
          - { mnt_path: "/mnt/media", nfs_host: "truenas.plumbus.lab", share_path: "/mnt/Media" }
      roles:
      - role: nfs_client

License
-------

BSD

Author Information
------------------

Derek Smiley - Aspiring System Administrator/Ansible Automation Engineer

Connect with me on LinkedIn - https://www.linkedin.com/in/derek-smiley/