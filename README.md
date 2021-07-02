Docker-Ombi
=========

A role to spin up a Ombi docker container. This role was heavily inspired by (and all credit goes to) Calvin Bui's roles. This is only being published for integration into my AWX instance. 

Requirements
------------

Docker needs to be installed and configured on the server. 

Role Variables
--------------

Required variables are listed here, along with default example values. See defaults/main.yml. Any of these defaults can be overwritten by using the vars role directory. 

    ombi_name: ombi

This is the name of the container. 

    ombi_image: linuxserver/ombi

The image container. By default this pulls from linuxserver.io.

    ombi_ports:
     - 8989:8989
     - 9898:9898

These are the exported ports of the container.

    ombi_config_directory: /opt/ombi

This is the directory that config files will be stored. This is mapped to /config in the container. 

    ombi_tv_directory: /tmp/tv

This is the directory that Ombi will move TV shows and managed files to. Usually we want this directory on some sort of media network storage. This is mapped to /tv inside the container.

    ombi_download_directory: /tmp/downloads

This is where files will be placed for Ombi to managed, either via a download client or manually. This is mapped to /completed inside the container.

    ombi_environment_variables:
      PUID: "1000"
      PGID: "1000"
      TZ: America/Chicago

This is a dictionary of extra environment variables for the container. 

    ombi_docker_additional_options:
      restart_policy: unless-stopped

NOTE: There have been variables added for a media user. Please see the vars/main.yml file for an example. 

Dependencies
------------

None.

Example Playbook
----------------

    - name: Deploy the Ombi Container.
      hosts: rr
      become: true
      roles:
      - role: docker-ombi

License
-------

BSD

Author Information
------------------

Derek Smiley - Aspiring System Administrator/Ansible Automation Engineer

Connect with me on LinkedIn - https://www.linkedin.com/in/derek-smiley/