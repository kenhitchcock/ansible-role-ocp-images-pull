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

Most variables required for this role to run are currently set in the defaults directory of the role and dont need to be set. 

OpenShift Versioning variables. Default values set to the following already.
     ocp_version: v3.11.146
     image_inspector_version: 2.1
     etcd_version : 3.2.22

Do you want to pull images, sometimes you just want to run the role again to export tar file. Default value set to "yes"
     ocp_images_pull_core: "yes"
     ocp_images_pull_app: "yes"
     ocp_images_pull_opt: "yes"

If you require images to be saved to a tar file, do not change the default values below.
     rhexport_core: "yes"
     rhexport_apps: "yes"

Path for exports
     rh_ocp_export_path_core: /var/lib/docker/overlay2/export/core.tar
     rh_ocp_export_path_app: /var/lib/docker/overlay2/export/app.tar


## Required variables
However you will need the following.

Red Hat token credentials to access the registry. You need to create a token at access.redhat.com
     rhreg_user: 
     rhreg_pass: 
     rhreg_name: "registry.redhat.io"


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

