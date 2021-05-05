Docker-Sonarr
=========

A role to spin up a Sonarr docker container. This role was heavily inspired by (and all credit goes to) Calvin Bui's role. Find this role [here](https://github.com/calvinbui/ansible-sonarr-docker).This is only being published for integration into my AWX instance. 

Requirements
------------

Docker needs to be installed and configured on the server. 

Role Variables
--------------

Required variables are listed here, along with default example values. See defaults/main.yml. Any of these defaults can be overwritten by using the vars role directory. 

    sonarr_name: sonarr

This is the name of the container. 

    sonarr_image: linuxserver/sonarr

The image container. By default this pulls from linuxserver.io.

    sonarr_ports:
     - 8989:8989
     - 9898:9898

These are the exported ports of the container.

    sonarr_config_directory: /opt/sonarr

This is the directory that config files will be stored. This is mapped to /config in the container. 

    sonarr_tv_directory: /tmp/tv

This is the directory that Sonarr will move TV shows and managed files to. Usually we want this directory on some sort of media network storage. This is mapped to /tv inside the container.

    sonarr_download_directory: /tmp/downloads

This is where files will be placed for Sonarr to managed, either via a download client or manually. This is mapped to /completed inside the container.

    sonarr_environment_variables:
      PUID: "1000"
      PGID: "1000"
      TZ: America/Chicago

This is a dictionary of extra environment variables for the container. 

    sonarr_docker_additional_options:
      restart_policy: unless-stopped

Another dictionary, this time of additional options for the container. By default, this sets the container to start on boot unless it was previously stopped. 

    sonarr_config:
      ApiKey: "abc123"
      UrlBase: "example.com"
      LaunchBrowser: "False"
      AnalyticsEnabled: "False"

This is not currently in use - the applicable code is commented out in the task. 

Dependencies
------------

None.

Example Playbook
----------------

    - name: Deploy the Sonarr Container.
      hosts: rr
      become: true
      roles:
      - role: docker-sonarr

License
-------

BSD

Author Information
------------------

Derek Smiley - Aspiring System Administrator/Ansible Automation Engineer

Connect with me on LinkedIn - https://www.linkedin.com/in/derek-smiley/