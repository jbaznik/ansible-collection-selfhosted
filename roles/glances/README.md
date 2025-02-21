# selfhosted.glances

Installs [Glances](https://nicolargo.github.io/glances/) - a cross-platform system monitoring tool.

## Role Variables

- `glances_version`
  - Default: `latest-full`
  - Description: The version of Glances to install. See [tags](https://hub.docker.com/r/nicolargo/glances/tags).
  - Type: str
  - Required: no
- `glances_webui_port`
  - Default: `61208`
  - Description: The port on which Glances' web interface will be accessible.
  - Type: int
  - Required: no
- `glances_server_port`
  - Default: `61209`
  - Description: The port on which Glances' server is listening.
  - Type: int
  - Required: no
- `glances_install_dir`
  - Default: `/opt/docker/glances`
  - Description: The directory where Glances will be installed.
  - Type: str
  - Required: no
- `glances_password`
  - Default: `changeme`
  - Description: The password for the Glances web interface.
  - Type: str
  - Required: no
- `glances_fs_volumes`
  - Default: `[]`
  - Description: A list of directories to mount on the Glances container. Will be mounted in "ro" mode.
  - Type: list
  - Required: no
- `glances_docker_settings`
  - Default: See [glances_docker_settings_default](./vars/main.yml)
  - Description: Docker container settings.

## Dependencies

- [community.docker](https://docs.ansible.com/ansible/latest/collections/community/docker/index.html)

## Example Playbook

```yaml
- hosts: localhost

  roles:
    - artyorsh.selfhosted.glances
``` 