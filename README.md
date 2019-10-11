Role Name
=========

name: ansible-role-image-pull
The purpose of this role is to pull all of the required runtime images from a connected environment. 
After the images are pulled they are exported to a tar.gz file.

Requirements
------------

Docker is installed
Docker daemon is running
All repo's are setup correctly 

Roles are available to do the above if required.

Role Variables
--------------

All variable required for this role to run are currently set in the defaults directory of the role

Example Playbook
----------------

- name: OpenShift Disconnected Prep 
  hosts: localhost  
  become: true

  tasks:
    - name: "Include the image pull role"
      include_role:
        name: ../roles/ansible-role-ocp-image-pull


License
-------

MIT

