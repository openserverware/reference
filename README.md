# A (very brief) introduction

This project contains an Ansible playbook.

When run, it first configures a host machine.
It does some simple configuration for OpenSSH and it installs Docker.

Then Ansible roles are used to deploy/configure applications.
One Ansible role is used for each application.

Ansible roles are used to load Docker images onto hosts and run images as containers.
To run images, it uses the Docker compose approach, using YAML.

Currently the following applications are included in this reference:

- A reverse proxy and let's encrypt certificate manager
- A static website (Apache)
- A cloud server (Nextcloud)
- A metrics application (cAdvisor, Prometheus, Grafana)

# How to run this?

Running it should be as simple as entering:

      ansible-playbook --limit vagrant_machine --tags up site.yml

Note:

   - Don't forget to add the www.myvagrant.nl, cloud.myvagrant.nl and metrics.myvagrant.nl names to your /etc/hosts file
   - To request let's encrypt certificates, set host variable 'letsencrypt_certificates: true'
   - To get test certificates, set host variables '\<role\>\_letsencrypt\_test\_certificates: true'
   - To get production certificates, set host variables '\<role\>\_letsencrypt\_test\_certificates: false'

Please read the site.yml documentation to find out about its backup and restore features.

# What can be improved?

The output is not (yet) suitable for public cloud infrastructure use.

Things that come to mind that are to be done:

- Finish the firewall configuration
- Put container data on an encrypted partition
- ...

# What do I hope to achieve with this project?

*Make it easy to manage open source server applications.*

*In particular for small private, community and business use.*
