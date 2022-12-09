# shinyproxy-hardened

This is a set of playbooks for deploying ShinyProxy with significant added security hardening.

The fundamental security limitations of ShinyProxy's design still remain, but are partially mitigated.

It is tested on RHEL 8 compatible distros and requires selinux to be in enforcing mode.

This config may break Docker Swarm or Kubernetes ShinyProxy backends, and may break some ShinyProxy authentication methods. It is not tested on ShinyProxy configurations that I do not use.

The following hardening methods are used:

* Docker is run in userns-remap mode
* Docker daemon is started with ```--no-new-privileges``` and ```--selinux-enabled```
* ShinyProxy is run with extensive systemd security hardening / sandboxing enabled


Todo
* Custom SELinux policy for ShinyProxy (currently runs unconfined)
* TLS termination via nginx or caddy
** ShinyProxy should be configred to run on port 8008 for compatibility with existing httpd SELinux policy


