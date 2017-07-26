# A (very brief) introduction

This project contains an Ansible playbook.

Firstly it is designed to configure a host machine.
It does some simple configuration for OpenSSH and it installs Docker.

More work has gone into the Ansible roles.
It uses Ansible roles to load Docker images on hosts.
To run them as containers, it uses the Docker compose approach, with YAML,just like how Ansible itself defines structure.
One Ansible role is used for each application. Each application can consist of one or more containers.

Note:

      Unfortunately this demo does not show how loaded Docker images can be used as reference to build a new image.
      Maybe I'll add a role that does that later. It will make this reference project more complete.

Currently the following applications are included in this demo:

- A reverse proxy and let's encrypt certificate manager
- Apache
- Nextcloud

# How to run this?

Running it should be as simple as entering:

      ansible-playbook --limit vagrant_machine --tags up site.yml

Note:

   - Don't forget to add the www.myvagrant.nl and cloud.myvagrant.nl domain names to your /etc/hosts file
   - To request let's encrypt certificates, set 'letsencrypt_certificates: true'
   - To get test certificates set '\<role\>\_letsencrypt\_test\_certificates: false'
   - To get certificates set '\<role\>\_letsencrypt\_test\_certificates: true'

Please read the site.yml documentation to find out about its backup and restore features.

# What can be improved improved?

The output is not suitable for public cloud infrastructure use.
Things that come to mind that are to be done:

- Finish the firewall integration
- Put container data on an encrypted partition
- ...

# What do I hope to achieve with this project?

*Make it easy to implement and maintain open source server applications.*
*In particular for small private, community and business use.*

# Why am I sharing this?

I'm sharing this project hoping to receive your feedback.
I will consider any changes to improve it as a reference implementation and
help it achieve its purpose (as just mentioned).

...and to find a job;-)
