# selfhosted.olivetin

Installs [Olivetin](https://www.olivetin.app) - a simple access to predefined shell commands from a web interface.

## Role Variables

- `olivetin_version`
  - Default: `latest`
  - Description: The version of Olivetin to install. See [tags](https://hub.docker.com/r/jamesread/olivetin/tags).
  - Type: str
  - Required: no
- `olivetin_port`
  - Default: `1337`
  - Description: The port on which Olivetin will be accessible.
  - Type: int
  - Required: no
- `olivetin_install_dir`
  - Default: `/opt/docker/olivetin`
  - Description: The directory where Olivetin will be installed.
  - Type: str
  - Required: no
- `olivetin_env`
  - Default: See [olivetin_env_default](./vars/main.yml)
  - Description: Docker container environment variables.
  - Type: dict
  - Required: no
- `olivetin_config`
  - Default: See [olivetin_config_default](./vars/main.yml)
  - Description: The contents of `config.yaml`. See [docs](https://raw.githubusercontent.com/OliveTin/OliveTin/main/config.yaml).
  - Type: dict
  - Required: no
- `olivetin_docker_settings`
  - Default: See [olivetin_docker_settings_default](./vars/main.yml)
  - Description: Docker container settings.
  - Type: dict
  - Required: no

## Dependencies

- [community.docker](https://docs.ansible.com/ansible/latest/collections/community/docker/index.html)

## Example Playbook

```yaml
- hosts: localhost

  roles:
    - artyorsh.selfhosted.olivetin
``` 