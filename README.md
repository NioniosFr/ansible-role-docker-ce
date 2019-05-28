Ansible Role: Docker CE
=========

An ansible role to install docker in RHEL based systems from the docker repository.

Requirements
------------

The role targets RHEL based systems build on the `x86_64` architecture.

The role is intended to run both on the controller and remote machines, which means that internet connectivity is required for both.

Role Variables
--------------

Default:

```yaml

docker_user: "docker" # A dedicated user for docker engine
docker_group: "docker" # A dedicated group for docker engine

docker_version: "18.09.6" # (Optional) Define a version to only try and install the given version (might cause failures if version is too old).

docker_proxy_env: [] # If you are behind a proxy, setup the following variables to create a proxy config file for the docker client.
  # http_proxy: "" # Optional-Required
  # https_proxy: "" # Optional
  # no_proxy: "" # Optional

```

Dependencies
------------

- `pip`
- `docker-py` - Latest version will be installed by this role via `pip`.
- `yum-utils` - Installed by the role
- `device-mapper-persistent-data` - Installed by this role
- `lvm2`- - Installed by this role

Example Playbook
----------------

```yaml
    - hosts: localhost
      become: true
      roles:
        - role: nioniosfr.docker_ce

    - hosts: localhost
      become: true
      roles:
        - role: nioniosfr.docker_ce # Install user and group. The user and group will be created and need to be dedicated to docker only.
          vars:
            docker_user: "my-custom-user"
            docker_group: "my-custom-group"
```

License
-------

MIT

Author Information
------------------

[NioniosFr](https://github.com/NioniosFr)
