# ansible-role-haproxy

This role installs the haproxy server, running in a Docker container on the target machine,
and links it to another container in order to provide SSL for the backend service.

## Requirements

This role requires Ansible 1.4 or higher

## Dependencies

- docker
- pip

## Role Variables

The variables that can be passed to this role and a brief description about
them are as follows with defaults shown:

```yaml
# haproxy Docker image name at DockerHub
haproxy_docker_image: haproxy:1.5

# Path on target machine to mount as Jenkins' home
haproxy_base_dir: /home/{{ansible_ssh_user}}/haproxy

# if true, all http traffic will redirect to https
haproxy_redirect_all_to_https: true

# backend host:port info
haproxy_backend_server: jenkins:8080

# backend docker container name (for linking)
haproxy_backend_container: jenkins

# create new self-signed cert at startup?
haproxy_new_cert: true

# if haproxy_new_cert is true, the fully qual' domain name to use for the SSL cert
haproxy_fqnd: jenkins.cloudbuilders.local

# if haproxy_new_cert is false, pass pem in with these (pem = BASE64 crt and key files concatenated into one file)
haproxy_ssl_crt: TODO-Find-best-way-to-pass-pem-file-in.

```

## Examples

- hosts: somehost
  sudo: yes
  remote_user: someuser

  roles:
    - haproxy

# License and Copyright

Copyright 2015 VMware, Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

## Author Information

This role was created in 2015 by [Eric Smalling / VMware](http://www.vmware.com/).

