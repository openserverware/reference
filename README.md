# A (very brief) introduction

This project contains an Ansible playbook.

When run, it first configures a host machine.
It does some configuration for OpenSSH and it installs Docker.

Then Ansible roles are used to deploy/configure applications.
One Ansible role is used for each application.

To deploy/configure applications, Ansible roles load Docker images onto the host machine.
For each Docker image, Docker Compose data is included in the Ansible role (in YAML format).
Docker Compose is used with the image and corresponding data to run application containers.

The following applications are included in this reference:

- A reverse proxy and Let's Encrypt certificate manager
- A static website (Apache)
- A cloud server (Nextcloud)
- A metrics application (cAdvisor, Prometheus, Grafana)

# Running the playbook

The Ansible playbook has been tested on a Vagrant machine running a Debian Jessie/Stretch box.
It should be no problem to run this on any other Debian Jessie/Stretch machine.
Just make sure the inventory/hosts file in the project contains the correct ip address, port number, etc.

To deploy the applications, enter:

      ansible-playbook --limit vagrant_machine --tags up site.yml

The following domain names are defined in the playbook and used by the reverse proxy to provide access to the applications:

    www.myvagrant.nl, 
    cloud.myvagrant.nl 
    metrics.myvagrant.nl 

...you will need to add them to your `hosts` file or find some other way to resolve them.

After the playbook has completed running and domain names can be resolved, the applications should be accessible from your internet browser.    

The following support for Let's Encrypt certificates is included in the playbook:

   - To request Let's Encrypt certificates, set host variable 'letsencrypt_certificates: true'
   - To get test certificates, set host variables '\<role\>\_letsencrypt\_test\_certificates: true'
   - To get production certificates, set host variables '\<role\>\_letsencrypt\_test\_certificates: false'

Application data backup and restore features are included in the playbook.
You can learn more about that (and other playbook features) from the documentation in the project `site.yml` file.

# What can be improved?

The playbook is not (yet) suitable for deploying applications to a public cloud infrastructure.
At least the following should be considered:

- Finish the firewall configuration
- Container data should be relocated to a /home directory (and be encrypted)
- ...

# What do I hope to achieve with this project?

*Make it easy to manage open source server applications.*

*In particular for small private, community and business use.*
